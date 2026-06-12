---
title: "apt-get dist-upgrade"
date: 2009-12-03
forum: General Help
---

### Post by Foxcow on 2009-12-03
Can anyone explain what this command does?  I have searched google and all of the info I have read suggests that this command updates existing packages and may install new ones.  It didn't sound risky so I ran it.  It ran for about 3 minutes or so while I was working and I noticed that some processes were no longer responding and menu items disappeared.  I tried to reboot but my system wouldn't respond.  I hit the restart button but got a grub error 15.

I searched for some info on the net and everything suggested that I start with a live CD.  I could not even get the live CD to boot (tried 3 different CDs) so I am at a loss.

Does anyone have any suggestions?

---

### Post by Bachstelze on 2009-12-03
dist-upgrade will upgrade all your installed packages, removing some or installing new ones if needed. This contrasts with upgrade, which will not upgrade a package if that requires removing an installed package or installing a new one.

---

### Post by jegerjensen on 2009-12-03
Have you successfully booted from cd on that computer before?  You may need to change some settings in BIOS in order to boot from cd.

---

### Post by Foxcow on 2009-12-03
I've used a live CD before 9.10 but for some reason, my machine won't boot this time using one.


Normally, this wouldn't be an issue as I would just format the partition and reinstall.  However, I have a registered copy of XP in Virtualbox that I don't want to lose.

---

### Post by Foxcow on 2009-12-03
> **Bachstelze said:**
> dist-upgrade will upgrade all your installed packages, removing some or installing new ones if needed. This contrasts with upgrade, which will not upgrade a package if that requires removing an installed package or installing a new one.

Has this been known to harm an install?  I figured it could not hurt.

---

### Post by Foxcow on 2009-12-03
Ok, I am now able to boot via liveCD but after that, I can't seem to restore my install of 9.10.


apt-get dist-update really broke my system and I have no idea how to fix it.

---

### Post by endBc on 2009-12-03
Check this [article]("http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/"). Might help you solve this problem.

---

### Post by Foxcow on 2009-12-03
This is what I get:

```

ubuntu@ubuntu:~$ sudo fdisk -l | grep -i linux
/dev/sda5           14348       14469      979933+  82  Linux swap / Solaris
/dev/sda6           14470       30401   127973758+  83  Linux

```


That looks fine but when I check my menu.lst, all appears to be right as well.  I am running 9.10 and Grub 1.5.

```

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		ef85eed2-18fd-4c66-a842-43e2d542c71d
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=ef85eed2-18fd-4c66-a842-43e2d542c71d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		ef85eed2-18fd-4c66-a842-43e2d542c71d
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=ef85eed2-18fd-4c66-a842-43e2d542c71d ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		ef85eed2-18fd-4c66-a842-43e2d542c71d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ef85eed2-18fd-4c66-a842-43e2d542c71d ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		ef85eed2-18fd-4c66-a842-43e2d542c71d
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=ef85eed2-18fd-4c66-a842-43e2d542c71d ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		ef85eed2-18fd-4c66-a842-43e2d542c71d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

```

---

### Post by Foxcow on 2009-12-04
Can anyone help?  I have been trying different things and nothing is working.  I have no clue what to do...

---

### Post by jegerjensen on 2009-12-04
How far do you get in the boot sequence?  What is the last thing you see on screen?

---

### Post by Foxcow on 2009-12-04
> **jegerjensen said:**
> How far do you get in the boot sequence?  What is the last thing you see on screen?

Error 15: File not found.



I can't use recovery mode either.

---

### Post by jegerjensen on 2009-12-04
Have you tried the solution endBc linked to?

```
root        (hd0,5)
```
and
```
root=/dev/sda6
```

---

### Post by Foxcow on 2009-12-04
I'll try it again just to make sure.

---

### Post by Foxcow on 2009-12-08
I could not get anything to work.  I finally had to format.  I lost all of my info :(

---

