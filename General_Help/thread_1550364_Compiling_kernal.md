---
title: "Compiling kernal"
date: 2010-08-11
forum: General Help
---

### Post by seandude on 2010-08-11
So, I decided to try installing the newest kernel.

I found what seemed to be a fairly good guide ([http://www.crashcourse.ca/wiki/index.php/New_kernel_on_Ubuntu_10.04](http://www.crashcourse.ca/wiki/index.php/New_kernel_on_Ubuntu_10.04)), but when I got to the point where I type in [FONT="Courier New"]make[/FONT], I get this for output:

[INDENT]
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CALL    scripts/checksyscalls.sh
  CHK     include/generated/compile.h
  VDSOSYM arch/x86/vdso/vdso-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-int80-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-syscall-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-sysenter-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-syms.lds
  LD      arch/x86/vdso/built-in.o
  LD      arch/x86/built-in.o
  CC [M]  fs/9p/vfs_inode.o
fs/9p/vfs_inode.c: In function ‘v9fs_vfs_setattr_dotl’:
fs/9p/vfs_inode.c:1267: error: implicit declaration of function ‘inode_setattr’
make[2]: *** [fs/9p/vfs_inode.o] Error 1
make[1]: *** [fs/9p] Error 2
make: *** [fs] Error 2
[/INDENT]

And now I can't move forward.  Nothing's installed, so no harm done, but I'd like to get this thing working.  Does anyone know what the error message 
[FONT="Century Gothic"]
fs/9p/vfs_inode.c:1267: error: implicit declaration of function 'inode_setattr’
make[2]: *** [fs/9p/vfs_inode.o] Error 1
make[1]: *** [fs/9p] Error 2
make: *** [fs] Error 2[/FONT]

means, and how I can fix this?

---

### Post by inameiname on 2010-08-11
Personally it's easier to just type this in the terminal and add the already compiled versions of the latest kernels:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-14-generic linux-image-2.6.35-14-generic

OR another option is using kernelcheck, which will make a customized kernel for your computer based on either standard settings or ones that you tweak:

(Not that any of this helps you specifically with your particular issue with the failed installation. :P But it's a potential option if you are merely wanting to install the latest kernel.)

---

### Post by seandude on 2010-08-12
Thanks for the help.  And yeah, that doesn't exactly help to explain why the installation failed.  I'm doing this more as an educational thing than a "I want the latest and greatest" (though that doesn't hurt).

Just out of curiosity, why do you use aptitude in the second command as opposed to apt-get?

---

### Post by seandude on 2010-08-12
Also, I'm now using the kernelcheck that you sent me (working pretty well), and I was wondering what the differences there were (effectively) between choosing to load an option as a module as opposed to just saying yes.

For example; I have the fan driver, and can just load it into the kernel, or can have it loaded as a module.  What are the differences?

---

### Post by inameiname on 2010-08-12
No prob. I can understand that. 

As far as using 'aptitude', it's just what I prefer over 'apt-get'. There isn't a whole lot of a difference. I've just found it less likely to miss installing all the dependencies and removing less when uninstalling something so I tend to stay more with 'aptitude', that's all. Plus, for experts, there are more options with 'aptitude' over 'apt-get'.

And about your question on modules, I'm afraid I don't really know. Good question though. Maybe this will help you: [http://www.ibm.com/developerworks/linux/library/l-lkm/](http://www.ibm.com/developerworks/linux/library/l-lkm/) and [http://tldp.org/HOWTO/Module-HOWTO/](http://tldp.org/HOWTO/Module-HOWTO/). Not to say they directly answer your question. I'm curious about that myself now.

---

### Post by pbrane on 2010-08-12
Yet another way to compile and install a kernel:
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

I use this method and it works great.

As for the modules; device drivers can be built as separate modules instead of as part of the kernel. That way the kernel will only load the drivers needed by the system you are running on. This way a lot of drivers can be compiled as modules thus supporting a wide range of systems and still keep the kernel small for faster loading.

---

### Post by seandude on 2010-08-12
So an update on my compiling adventure.  The computer doesn't boot now that I've used kernelcheck.  I'm currently running off a live-cd I had lying around.  I think the problem is that I didn't update grub after installing kernelcheck did it's thing.  I'm going to try that now, but if that doesn't work, I'm really not sure what will. 

Kernelcheck also told me that I would need to reinstall my NVidia driver after I rebooted, but I don't think that's the problem, because boot doesn't even finish.  

Any suggestions?

---

### Post by pbrane on 2010-08-12
I'm not familiar with kernelcheck, but your nvidia driver probably needs to be re-installed. With the make-kpkg method from the link above you won't have that issue. Check to see if kernelcheck created a new initrd.img in the /boot directory, and updated grub.

What I've been doing is download the latest stable kernel from kernel.org and then follow the *Using Ubuntu Kernel Configuration* directions from the link above.

---

### Post by seandude on 2010-08-12
It didn't make a new initrd.img.  How do I do that?

It also didn't update grub.  When I tried to though, it wouldn't let me.  The error message I got was

"grub-probe: error: cannot find a device for /."

I'm guessing this is because I'm running off of a live disk.  How to I make it so that the command affects *my* machine?

---

### Post by pbrane on 2010-08-12
You should boot to your previous kernel and have a look at **man  mkinitramfs**.

---

### Post by seandude on 2010-08-12
I actually found the error message I was getting on the Linux Kernel Howto.

[COLOR=#000000]Warning: unable to open an initial console
	Kernel panic: no init found. Try passing init= option to kernel

I just don't know how to correct this.  I'm hoping that it's explained in the forums a little further on.
[/COLOR]

---

### Post by seandude on 2010-08-12
I think I've figured out how to fix everything, but I have one problem.  I can't seem to get into the grub menu from boot.  Do you know how?

I also can't seem to figure out how to boot with a different kernel.  This was what I tried to do when I began, but I couldn't remember the button combination to get into it.  I've tried holding shift, delete and esc.  I can't find it anywhere on the internet.  What is it?

---

### Post by pbrane on 2010-08-13
Hold down the shift key while booting, before you get to grub, IIRC.

---

