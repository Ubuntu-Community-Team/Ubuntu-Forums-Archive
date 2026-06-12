---
title: "converting integer to binary"
date: 2012-03-23
forum: General Help
---

### Post by nataliafoster26 on 2012-03-23
here is my code i segmentation fault dont know why
```





; ******************************************************************
;  Convert integer to ASCII/Binary string.
;    Note, no error checking required on integer. ; -----
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

```

---

### Post by jonobr on 2012-03-23
Hey there


You may try posting in the programming section,
There are lots of posts in general help so it would be visible longer over there and may draw the attention of more knowledge scripting/programming folks

---

