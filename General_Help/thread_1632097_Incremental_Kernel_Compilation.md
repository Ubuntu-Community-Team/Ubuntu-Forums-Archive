---
title: "Incremental Kernel Compilation"
date: 2010-11-27
forum: General Help
---

### Post by Sethu85 on 2010-11-27
As part of a course , i am changing the net/ipv4 code and i would like to boot the kernel with these changes .. 

I am using Jaunty and i followed the instructions @ [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) and 

[http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/](http://blog.avirtualhome.com/2009/09/08/how-to-compile-a-kernel-for-ubuntu-jaunty-revised/)

I am changing the code in /net/ipv4/fib_hash.c for this project.

I would like to know how i can do incremental compiling of the kernel. As i am a beginner , i can not write clean code in my first attempt. And I find it frustrating to wait for 2 hours to know that i have made an error in the logic of my code.

Is there any way to make only the /net/ipv4 module and and .o file that would be generated, is automatically linked in the new kernel image quickly, instead of building the kernel image completely after a small change in the /net/ipv4/fib_hash.c code.

Thanks for any help.

PS: I find someone had the same problem at [http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/) (in the comments section "Pav"). And there was no solution posted there as well.

---

### Post by andrewthomas on 2010-11-27
Look at the first question and answer at 

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

---

