---
title: "Segmentation fault when memory demand is high"
date: 2009-08-06
forum: General Help
---

### Post by whaler1 on 2009-08-06
Hi all,
 
I am trying to solve large matrices with a fortran command line executable matrix solver that is compiled with the Linux version of the Intel compiler.  I am using Ubuntu ver. 8.1 on a Dell that has 8Gb of RAM and a i7 processor.  When the size of the matrix exceeds about 80000^2 indices the solver crashes with a segmentation fault message, smaller matrices are no problem.  On my XP laptop with 2Gb of RAM I can solve much larger matrices with the same solver code no problem at all.  I am wondering if there is something I need to do with the Ubuntu configuration in order to allocate more memory to my solver.  
 
As alway, any help is appreciated.

---

### Post by Johnny B on 2009-08-06
i would do a memtest from grub at boot

---

### Post by whaler1 on 2009-08-06
When I try to boot into memtest86+ I get the message; Error 28: Selected item cannot fit into memory.

---

### Post by whaler1 on 2009-08-06
Following up on this problem, can anyone interpret what the following 'displaymem'
output means?  and what would be even better, does it indicate that all of my 8GB of RAM is recognized?
 
grub> displaymem
EISA Memory BIOS Interface is present
Address Map BIOS Interface is present
Lower memory: 602K, Upper memory (to first chipset hole): 3136064K
[Address Range Descriptor entries immediately follow (values are 64-bit)]
Ussable RAM: Base Address: 0x0  X 4GB + 0x0,
 Length: 0x0 X 4GB + 0x96800 bytes
Reserved: Base Address: 0x0 X 4GB + 96800,
 Length: 0x0 X 4GB + 0x9800 bytes
Reserved: Base Address: 0x0 X 4GB + 0xe0000,
 Length: 0x0 X 4GB + 0x20000 bytes
Ussable RAM: Base Address: 0x0  X 4GB + 0x100000,
 Length: 0x0 X 4GB + 0xbf690000 bytes
Reserved: Base Address: 0x0 X 4GB + 0xbf790000,
 Length: 0x0 X 4GB + 0xe000 bytes
Reserved: Base Address: 0x0 X 4GB + 0xbf79e000,
 Length: 0x0 X 4GB + 0x32000 bytes
Reserved: Base Address: 0x0 X 4GB + 0xbf7d0000,
 Length: 0x0 X 4GB + 0x10000 bytes
Reserved: Base Address: 0x0 X 4GB + 0xbf7ec000,
 Length: 0x0 X 4GB + 0x14000 bytes
Reserved: Base Address: 0x0 X 4GB + 0xbf800000,
 Length: 0x0 X 4GB + 0x800000 bytes
Reserved: Base Address: 0x0 X 4GB + 0xfee00000,
 Length: 0x0 X 4GB + 0x1000 bytes
Reserved: Base Address: 0x0 X 4GB + 0xffb00000,
 Length: 0x0 X 4GB + 0x500000 bytes
Ussable RAM: Base Address: 0x1  X 4GB + 0x0,
 Length: 0x1 X 4GB + 0x40000000 bytes

---

### Post by dcstar on 2009-08-06
> **whaler1 said:**
> Hi all,
 
I am trying to solve large matrices with a fortran command line executable matrix solver that is compiled with the Linux version of the Intel compiler.  I am using Ubuntu ver. 8.1 on a Dell that has 8Gb of RAM and a i7 processor.
.....

a) Only 64-bit OS's will fully utilise >4GB of RAM.

b) AFAIK 32-bit Ubuntu needs the Server kernel to use PAE which will allow a **single** process to use up to 4GB of available RAM - otherwise you will be restricted to ~3.2GB with the standard kernel.

c) Linux pushes RAM hardware far harder than Windows, so RAM chips that will work on one OS can fail under Linux.

---

