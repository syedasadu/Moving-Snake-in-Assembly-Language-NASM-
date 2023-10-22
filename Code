[org 0x0100]
		jmp start
		
message:	db 'Asad->Sharaz'
len:		dw	12
count:		dd  0
road: 		dw  136,456,776,1096,1416,1736,2056,2376,2696,3016,3336,3656,3976
road2:		dw  160,480,800,1120,1440,1760,2080,2400,2720,3040,3360,3680,3996

clrscr:		push es
			push ax
			push di
			push si
			push cx
			
			mov ax, 0xb800
			mov es, ax
			mov di, 0
			
nextloc:	mov word[es:di], 0x0720
			add di, 2
			cmp di, 4000
			jne nextloc
			
			pop cx
			pop si
			pop di
			pop ax
			pop es
			ret
			
delay:		;a large loop for delaying next move
			mov dword[count],500000

further:	dec dword[count]
			cmp dword[count],0
			jne  further
			ret
			
printStr:	push bp
			mov bp, sp
			push es
			push ax
			push cx
			push si
			push di
			
			mov ax, 0xb800
			mov es, ax
			
			mov di, [bp+8]
			mov si, [bp+6]
			mov cx, [bp+4]
			mov ah, 0x04

nextchar2:	mov al, [si]
			mov [es:di], ax
			add di, 2
			add si, 1
			loop nextchar2
			
			pop di
			pop si
			pop cx
			pop ax
			pop es
			pop bp
			ret 6
		
		
start:		call clrscr
			mov di,0
			mov bx,0
			
repeaaat:	push di
			mov ax, message
			push ax
			push word[len]
			call clrscr
			call printStr
			call delay
	
			cmp di,[road+bx]
			je back2
			
			add di, 4
			cmp di, 3976
			jne repeaaat
			jmp done

back2:      add di,160

back:		push di
			mov ax, message
			push ax
			push word[len]
			sub di, 4
			call clrscr
			call printStr
			call delay
			cmp di,[road2+bx]
			jne back
			add di,160
			add bx,2
			jmp repeaaat

done:	
		mov ax, 0x4c00
		int 0x21
