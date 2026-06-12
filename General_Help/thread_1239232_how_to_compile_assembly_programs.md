---
title: "how to compile assembly programs??"
date: 2009-08-13
forum: General Help
---

### Post by burmanabhay88 on 2009-08-13
i need a compiler for assembly programs.
is there one for ubuntu?(as a debian package). preferably in the repos

I need to compile simple programs like
// print a to z
.model small

.stack 100h

.code



start:

mov dl,'a'

back:

mov ah,2h

int 21h

inc dl;

cmp dl,'z'

jne back

mov ah,2h

int 21h

mov ax,4c00h

int 21h

end start


I had posted earlier also, but no one replied
[http://ubuntuforums.org/showthread.php?p=7777858](http://ubuntuforums.org/showthread.php?p=7777858)

---

### Post by stlsaint on 2009-08-13
if you are using jaunty than just check the repos...there are many compilers there from what i have seen...

---

### Post by nikhilbhardwaj on 2009-11-25
there's nasm
but it wont compile the above code
its syntax is different

looks like you need masm611
i can verify that it works under dosbox perfectly
i used it this sem for my microprocessors paper

---

### Post by burmanabhay88 on 2009-11-25
> **nikhilbhardwaj said:**
> there's nasm
but it wont compile the above code
its syntax is different

looks like you need masm611
i can verify that it works under dosbox perfectly
i used it this sem for my microprocessors paper

thanks... but it's a really old post. got it working long time back. :)

---

