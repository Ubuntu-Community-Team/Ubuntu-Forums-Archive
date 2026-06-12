---
title: "Problem with latest kernel..."
date: 2006-02-16
forum: General Help
---

### Post by DarkAngel88 on 2006-02-16
Hi,

I just updated my kernel with the latest one from [www.kernel.org](www.kernel.org) (2.6.15.4) using the guide here to update the kernel to 2.6.14.x.  Everything when smooth except that when I boot into Ubuntu, I couldn't see the boot screen written "Ubuntu" with all the different modules loading.  Now this is bugging me because there is only a black screen... like if my computer had crashed !!  After a while, I get the login screen like normal....

I tried changing the boot screen using this tutorial : [http://wiki.ubuntu-fr.org/applications/usplash]("http://wiki.ubuntu-fr.org/applications/usplash") but when I type in the last command to compile the boot screen, I get this error : ```
~/Temp$ sudo dpkg-reconfigure linux-image-$(uname -r)
Package `linux-image-2.6.15.4' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.15.4 is not installed

```

Can someone help me out on this one please ??

Thank you very much !!

DA

---

### Post by RAOF on 2006-02-16
It seems you didn't build a kernel-image .deb.  You just ran "make ?config" "make modules" "make", etc?  In that case, I don't know how to fix your bootsplash.  But I can tell you that if you build a kernel .deb as per the [wiki guide]("https://wiki.ubuntu.com/KernelHowto"), you'll score the bootsplash for free :)

---

### Post by codejunkie on 2006-02-16
[QUOTE=DarkAngel88]Hi,

I just updated my kernel with the latest one from [www.kernel.org](www.kernel.org) (2.6.15.4) using the guide here to update the kernel to 2.6.14.x.  Everything when smooth except that when I boot into Ubuntu, I couldn't see the boot screen written "Ubuntu" with all the different modules loading.  Now this is bugging me because there is only a black screen... like if my computer had crashed !!  After a while, I get the login screen like normal....

I tried changing the boot screen using this tutorial : [http://wiki.ubuntu-fr.org/applications/usplash]("http://wiki.ubuntu-fr.org/applications/usplash") but when I type in the last command to compile the boot screen, I get this error : ```
~/Temp$ sudo dpkg-reconfigure linux-image-$(uname -r)
Package `linux-image-2.6.15.4' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.15.4 is not installed

```

Can someone help me out on this one please ??

Thank you very much !!

DA[/QUOTE]
i had the same problem and i got around the black screen problem with ```
sudo gedit /boot/grub/menu.lst
``` and remove the word splash from my kernel entry this solves the black screen problem but you still won't have usplash.

---

### Post by DarkAngel88 on 2006-02-16
What did you got instead of the black screen ??  I did the modification but still get the black screen.  I'll try RAOF advice and get back to you guys.  Thanks !

EDIT : I tried the wiki link but it's the same I did with the guide here...

---

### Post by RAOF on 2006-02-16
[QUOTE=DarkAngel88]...
EDIT : I tried the wiki link but it's the same I did with the guide here...[/QUOTE]
You mean, you rebuilt your kernel as a debian package, installed that, and **still** didn't get a bootsplash?  That's always worked for me.

What does 
```
dpkg -l | grep 2.6.15.4
```return?  If it doesn't return anything, you probably haven't properly built a deb of the kernel.  If it **does** return something, try "sudo dpkg-reconfigure <whatever_the_grep_returned>"

---

### Post by DarkAngel88 on 2006-02-16
Here is what I got : 

```
darkangel88@Dark-Laptop:~$ dpkg -l | grep 2.6.15.4
ii  kernel-image-2.6.15.4                  10.00.Custom Linux kernel binary image for version 2.6.15

```

I'll try reconfiguring the dpkg like you said ! Thanks for your help !

In the meantime (cause I'll reconfigure everything tomorrow..little tired right now ;) ) if someone know how to solve the problem without reconfiguring everything.. It will be appreciated !!

Thanks !

---

### Post by DarkAngel88 on 2006-02-17
Hmmm...  

I tried everything in the wiki guide without any success.  I still have the black screen and I still can't see a thing.  

I need help !!

---

