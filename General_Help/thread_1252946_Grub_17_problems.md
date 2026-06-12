---
title: "Grub 17 problems"
date: 2009-08-29
forum: General Help
---

### Post by Johhny Ridden on 2009-08-29
I found the topic in the archives but I found it a bit overwhelming, still really new to all this as well.

As it says in the topic title im getting error 17

It goes
[I]Grub is loading stage 1.5

Error 17

[/I]I tried to do a few things in the archive topic such as setting the HDD's to auto (they were already set as that) and tried this:
[I]When the installer installed GRUB using that data, it tried to install the first part of GRUB on /dev/sda and told it to look for the OS on /dev/sdc. Unfortunately, this translated to "install on (hd0) then look for the OS on (hd2)", so it was looking for the OS on the wrong drive.

To fix it, you have to teach GRUB which order the BIOS uses.  To do this, follow these steps:

1) Boot from the Ubuntu CD
2) Open a Terminal (Applications->Accessories->Terminal)
3) Run "sudo -s"
4) Run "mkdir /ubuntu"
5) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"
:cool: Edit device.map (using vi or another text editor)[/I]   

And it gives me
[I]ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# mkdir /ubuntu
root@ubuntu:~# mount /dev/sdc1 /ubuntu
root@ubuntu:~# chroot /ubuntu
chroot: cannot run command `/bin/bash': No such file or directory
root@ubuntu:~# cd /boot/grub
bash: cd: /boot/grub: No such file or directory
root@ubuntu:~# 


[/I]I don't have much experience with this and the archive is quite long and a bit confusing what other solutions are there?

---

### Post by SteveDee on 2009-08-30
Have a look at this: [http://ubuntuforums.org/showthread.php?t=1203368](http://ubuntuforums.org/showthread.php?t=1203368)

Error 17 usually means you have specified the wrong partition in your /boot/grub/menu.lst file.

---

### Post by Bucky Ball on 2009-08-30
> **SteveDee said:**
> Error 17 usually means you have specified the wrong partition in your /boot/grub/menu.lst file.

Exactly. You're just pointing at the wrong partition so you're pretty much there. 

[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

An excellent resource. ;-)

---

