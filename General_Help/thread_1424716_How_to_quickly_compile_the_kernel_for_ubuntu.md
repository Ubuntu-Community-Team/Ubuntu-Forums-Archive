---
title: "How to quickly compile the kernel for ubuntu?"
date: 2010-03-08
forum: General Help
---

### Post by bbzjdhs on 2010-03-08
I am not sure whether this is the right place to ask the question. I am a newbie for linux.
First, following the link
[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
I can compile and install the custom kernel.
I am writing a driver to ubuntu. I find i need to change some code(the export interface for my driver) in the kernel source. When finished this, then i type the following code(at root account):
make-kpkg clean
make-kpkg --initrd --append-to-version=-mycustom kernel_image kernel_headers
again, it is ok, my problem is that can i don't type the "make-kpkg clean"? I just do the modification for file "/drivers/mmc/core/sdio_io.c" , so i expect it compiles that file only and then produce the new kernel image to install. This will be much quickly, isn't it? Completely compile the kernel need nearly 2 hours for my laptop desk.
 
Could anyone tell me how to do that?
 
Thanks in advance.
 
bb

---

### Post by skymera on 2010-03-08
For more details on how to customise an Ubuntu kernel, look here:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I'm not 100% sure what you're asking for.

---

### Post by bbzjdhs on 2010-03-08
It seems that it tell me how to compile the kernel. My problem is how to recompile the kernel for little modification of the kernel source as quickly as possible.

Thank you all the same.

---

