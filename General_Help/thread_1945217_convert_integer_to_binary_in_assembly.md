---
title: "convert integer to binary in assembly"
date: 2012-03-22
forum: General Help
---

### Post by nataliafoster26 on 2012-03-22
any help will be appreaciated
```

; ******************************************************************
;  Convert integer to ASCII/Binary string.
;    Note, no error checking required on integer.

; -----
;  Arguments:
;    1) integer, value
;    2) string, address
; -----
;  Returns:
;    ASCII/Binary string (NULL terminated)

global    cvtIntToASCIIBinary
cvtIntToASCIIBinary:


;    YOUR CODE GOES HERE
push    ebp
mov    ebp, esp
push    eax
push    ebx
push    ecx
push    edx
push    esi
push    edi

mov eax,dword[ebp+8] ;get value of the number
mov ebx,dword[ebp+12], get the address of the string
mov ecx,8

convert:
mov edx,0
div dword[two]
mov byte[ebx],dl       ;save value 
inc ebx
loop convert

mov byte[ebx],NULL






pop    edi
pop    esi
pop    edx
pop    ecx
pop    ebx
pop    eax
mov    esp, ebp
pop    ebp

    ret

```what is not converting right any help will be appreaciated

---

### Post by quadproc on 2012-03-22
I am not sure exactly what you are trying to do so I will guess that you have ASCII characters in a text string which represents a decimal number, and you wish to convert this decimal number into a single word integer which represents that value.  If this assumption is incorrect then you will need to modify my suggested solution to suit your needs.

First, an assumption: your input string will convert to a number which will fit into a single word of storage.  Second, the number is positive or 0.

The procedure for converting an ASCII integer is very simple: clear the result, set a pointer to the start of the string, (label goes here) get a character from the byte at the pointer and autoincrement the pointer, if the character was a null (or was some other designated end-of-string character) then exit the procedure, multiply the old result by 10, convert the character by subtracting hex 30 from it, add the modified character to the result, go back to the label.  When the program exits the procedure it will have the answer in the result.

It might be helpful to write a simple C function to do this, and then to "compile" it with the -S option so that you get the assembly code for it, and compare that code to your assembly code.

Hope this helps.

quadproc

---

