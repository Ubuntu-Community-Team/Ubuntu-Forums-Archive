---
title: "c and c++ to assembly language"
date: 2011-03-10
forum: General Help
---

### Post by vivek.pandey on 2011-03-10
hey everyone
   is there anyway in ubuntu by which we can translate or convert a high level language such as c, c++ into an assembly level code?
what i mean is say i wrote a hello world program in c . i want some software or command which converts the code into an equivalent assembly level code.
hope i am clear
thanx in advance to all

---

### Post by TeoBigusGeekus on 2011-03-10
```
#include <stdio.h>
int main(void)
{
    printf("Oh hi there!\n");
    return 0;
}
```
Save as hi_there.c
Then
```
gcc -S hi_there.c
```
and a file called hi_there.s will be created:
```
	.file	"hi_there.c"
	.section	.rodata
.LC0:
	.string	"Oh hi there!"
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	andl	$-16, %esp
	subl	$16, %esp
	movl	$.LC0, (%esp)
	call	puts
	movl	$0, %eax
	leave
	ret
	.size	main, .-main
	.ident	"GCC: (GNU) 4.5.2 20110127 (prerelease)"
	.section	.note.GNU-stack,"",@progbits
```

---

### Post by vivek.pandey on 2011-03-10
> **TeoBigusGeekus said:**
> ```
#include <stdio.h>

and a file called hi_there.s will be created:

```

thanx for this line actully i was trying this command 

vivek@NEO:~$ gcc -S -o example1.s example1.c
 for long but i didnt know a file called exampple.s would be created. i had presumed as sonn as a type that command i will get the output as the assembly code and now i opened the file called example.s and here i go , got the assembly code..
thanx a lot

---

### Post by vivek.pandey on 2011-03-10
is there anyway to assemble this assembly code and see the output?
i tries nasm example1.s
but that showed a  whole bunch of errors

---

### Post by TeoBigusGeekus on 2011-03-10
That's because gcc creates GAS (gnu assembler - AT&T) compatible code and not nasm (intel) code.
Try with 
```
gcc hi_there.s -o hi_there
```
and run it with
```
./hi_there
```

---

