---
title: "What's the easiest way to try kernel 2.6.32?  (re: Microsoft Integration Components)"
date: 2009-11-25
forum: General Help
---

### Post by sofakng on 2009-11-25
I'm testing out Microsoft's Hyper-V (under Windows Server 2008 R2) and I'd like to install Ubuntu Server as a virtual machine.

I've been trying to do some research and apparently the Microsoft/Linux integration components are part of Linux kernel 2.6.32.  Is this true?

What's the easiest way for me to get Ubuntu and use this kernel?

I've read a few guides on how to compile your own kernel, etc, but I'm wondering what method is really best for me to just try it out and see if the integration components actually work.

Thanks for any help!

---

### Post by sbrattonuk on 2009-12-02
I've been looking at Mythbuntu and I wanted the 2.6.32 kernel which had compatibility for my tuner card built in.

This was on a system I could afford to lose so 
I went to the kernel repository and manually downloaded one of the kernel packages (I can't remember which I used - it wasn't the kernel-headers)  and compiled this with make /makeinstall 

Bingo I had a working 2.6.32 kernel in Karmic.
one FS error appeared at next reboot and 2 days later the system hung terminally, 

At least I got to test my tuner card and see it working.

I'll be compiling in the required modules by hand next time using modprobe/insmod command once I know which modules I need.

 
Then there's the proper way to do it, 
goto How2forge and there's a very good description of how to do this for the major distros.

Please don't try my initial way unless you are prepared to restart from a fresh install.

Steven
(dangerous with a little bit of knowledge - and a system I could afford to rebuild)

---

### Post by sgosnell on 2009-12-02
No need to compile kernels, go to [the Ubuntu kernel site](http://kernel.ubuntu.com/~kernel-ppa/mainline/) and download the one you want.  You can install it with gdebi, the built-in package manager.

---

### Post by seeker5528 on 2009-12-02
If it is just the kernel you want to test, then you probably just want to download and install Karmic.

Lucid has already been using the 2.6.32 pre-release kernels, if you are more adventurous.

If you go the Karmic route you can get the source code for the kernel from upstream at:

[http://www.kernel.org/](http://www.kernel.org/)

: or get the version that includes patches done for Ubuntu by going to:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

: and searching for 'linux-source', with the distribution set to lucid.

If you don't want to get in to the nitty gritty of what to do with your kernel once it's compiled and would much rather end up with some .deb files so your custom kernel can be easily installed/removed, then kernel-package is for you. For a pretty easy to follow/bare minimum guide to the process using kernel-package look here:

[http://aligunduz.org/articles/buildkernel.html](http://aligunduz.org/articles/buildkernel.html)

Those instructions should work with Debian, Ubuntu, and pretty much any of their derivatives.

Later, Seeker

---

### Post by sbrattonuk on 2010-01-22
Found a really easy way to get 2.6.32 that is stable and works.

Install the ubuntu Kernel from 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

browse to the appropriate kernel folder eg 2.6.32

click on 
linux-headers-2.6.32-020632_2.6.32-020632_all.deb
once downloaded install with the deb package manager in ubuntu

then repeat for
linux-image-2.6.32-020632-generic_2.6.32-020632_i386.deb

Reboot, 
Open Terminal and type 
uname -a
To check the kernel version in use. 

Hope this helps.
can also be used for development versions of the kernel eg 2.6.32.4

I'd love to reference the post where I learnt this but I can't remember where I found it.  Thankyou anyway 

Steven

---

