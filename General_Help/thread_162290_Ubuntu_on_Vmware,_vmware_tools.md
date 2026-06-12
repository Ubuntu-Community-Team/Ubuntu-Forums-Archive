---
title: "Ubuntu on Vmware, vmware tools"
date: 2006-04-18
forum: General Help
---

### Post by jonsky on 2006-04-18
Hi there, I have just installed the wondrfull ubuntu operating system in vmware (xp host) and I am having slight problems installing vmware tools, it has made a virtual cd folder, and thats a far as I seem to get... can anyone help, im also a linux noob so please go easy on me :)

---

### Post by Ulokye on 2006-04-18
Can you explain the problem abit more? I am having a hard time understanding your real problem, this might solve your problem 

[http://www.vmware.com/support/gsx3/doc/tools_install_lin_gsx.html](http://www.vmware.com/support/gsx3/doc/tools_install_lin_gsx.html)

welcome to the linux community.

---

### Post by Computeruser on 2006-04-18
Read through the VMware documentation on installing the Tools in guest systems. In the Ubuntu docs, it notes that you must use the .tar file (not the .rpm file). So, here is how I did it with my (admittedly old) notes:

Make a folder of your choice in Ubuntu under the main root. I call mine /tools.
Open a terminal session.
mkdir /tools
chmod 777 /tools

Now make sure from the VMware menu that Install Tools is active.
Open a terminal session.
cd /tools
mount -t iso9660 /dev/cdrom /mnt
cp /mnt/ ...the tar file  /tools
umount /mnt
tar zxf ...the tar file
cd vmware-tools-distrib
./vmware-install.pl

accept the defaults and the Tools should install. 

If you get a compiler error, you have upgraded your kernel and the basic Tools install is a no-go. Come back and post. I have notes and I have done it, but it is not for the weak-of-heart.

Good luck.  I am pretty much a Linux noob as well, as Windows continues to fit my needs better and is my everyday system.

---

### Post by jonsky on 2006-04-23
thank you very much for your help...finaly managed it...much better :) im suprised how well ubuntu works, it works sweet even in this vitrual machine.

Again thanks

---

### Post by panjkov on 2006-04-23
Hi!
I Have vmware5 and ubuntu 5.1 and I am stuck to high resolution. when I try to change resolution, my vmware screen of ubuntu becomes messy and after a while, luckily, returns to that hi-res screen. Also, I am unable to install Tools, I receive compiler error. Help!

---

### Post by Computeruser on 2006-04-23
Panjkov - what kernel version are you running ? (uname -r)

---

### Post by panjkov on 2006-04-23
I solved problem:
I  installed required packages : make, kernel sources anf
others listed in message I received in config script, and after that again started config. This time, everything was OK.

---

### Post by Computeruser on 2006-04-23
That is good to hear. For kernel version 2.6.12-10-386, Article number 370579 in the VMware Community forums provides good information for installing the Linux source (which is a prerequisite for proper Tools installation).

---

