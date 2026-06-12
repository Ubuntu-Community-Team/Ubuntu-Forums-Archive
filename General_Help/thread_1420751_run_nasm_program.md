---
title: "run nasm program"
date: 2010-03-03
forum: General Help
---

### Post by muctadir on 2010-03-03
i am learning assembly language. i downloaded a code. the code is given below-

	SECTION .data		; data section
msg:	db "Hello World",10	; the string to print, 10=cr
len:	equ $-msg		; "$" means "here"
				; len is a value, not an address

	SECTION .text		; code section
        global main		; make label available to linker 
main:				; standard  gcc  entry point
	
	mov	edx,len		; arg3, length of string to print
	mov	ecx,msg		; arg2, pointer to string
	mov	ebx,1		; arg1, where to write, screen
	mov	eax,4		; write command to int 80 hex
	int	0x80		; interrupt 80 hex, call kernel
	
	mov	ebx,0		; exit code, 0=normal
	mov	eax,1		; exit command to kernel
	int	0x80		; interrupt 80 hex, call kernel

i am trying to run the program using following command
nasm -f hello.asm
gcc -o hello  hello.o
./hello

but i get an error after second command. 
/usr/bin/ld: i386 architecture of input file `hello.o' is incompatible with i386:x86-64 output
collect2: ld returned 1 exit status

i have a 64 bit kubuntu 9.10

thanks in advance..........

---

