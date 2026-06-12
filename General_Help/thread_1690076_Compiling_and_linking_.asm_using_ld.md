---
title: "Compiling and linking .asm using ld"
date: 2011-02-17
forum: General Help
---

### Post by kennny2004 on 2011-02-17
I wrote main.asm file that uses printf function.
> extern printf

however now when i compile it with
> 
nasm -f elf main.asm
ld -m elf_i386 -s -o main main.o


I get an error message 
> 
main.asm:(.text+0x6): undefined reference to `printf'


I am not sure what to try to make it work. I included "extern printf" in my .asm file. If someone could help me out that would be great. Thanks.

---

