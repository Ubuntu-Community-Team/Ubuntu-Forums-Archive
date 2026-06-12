---
title: "server 10.10 boot issues after fsck work"
date: 2010-11-14
forum: General Help
---

### Post by moo9801 on 2010-11-14
Hi all again,
I was editing my fsck at etc/fstab/ after removing a hard drive and i think i commented out the wrong drive :P. now i just get a blank screen on boot. I have the ability to use my ubuntu cd for a recovery console, live desktop, etc.  this is a webserver so i would like to try to have it fixed by Monday, i have customers, you know! :)

Thanks all,
moo9801

---

### Post by sohlinux on 2010-11-14
> **moo9801 said:**
> Hi all again,
I was editing my fsck at etc/fstab/ after removing a hard drive and i think i commented out the wrong drive :P. now i just get a blank screen on boot. I have the ability to use my ubuntu cd for a recovery console, live desktop, etc.  this is a webserver so i would like to try to have it fixed by Monday, i have customers, you know! :)

Thanks all,
moo9801

just boot with the live cd and remove the comment

---

### Post by moo9801 on 2010-11-14
I would do that, but could you give me the codes to enter on the live cd to do so? do i need the desktop or recovery console?

---

### Post by sohlinux on 2010-11-14
from the live cd desktop terminal 

```
 gksudo gedit /etc/fstab 
```

then remove the comment # which you put earlier

---

### Post by moo9801 on 2010-11-14
I don't know... It appears that i did'nt comment them out, i deleted, but i put one in according to the stats on the drive, but when i boot, i still see the blinking cursor in the upper left then it goes blank entirely, and thats it.

---

### Post by sohlinux on 2010-11-14
did you run the recovery option?

---

### Post by moo9801 on 2010-11-14
> **sohlinux said:**
> did you run the recovery option?

give me a sec ill try...  you mean the recovery console?

---

### Post by sohlinux on 2010-11-14
> **moo9801 said:**
> give me a sec ill try...  you mean the recovery console?

yes

---

### Post by sohlinux on 2010-11-14
you can use Pysdm from the live cd to fix your fstab

---

### Post by moo9801 on 2010-11-14
So I would type what into the recovery console? or the desktop termanal?  I've had a server for a while, but 0 troubleshooting skills. :P I'm running a small business for computer support, but thats windows :D

---

### Post by sohlinux on 2010-11-14
you can use Pysdm from the live cd to fix your fstab

its on the live cd desktop menu under system - administraion - storage device manager

---

### Post by moo9801 on 2010-11-14
oddly enough i didn't find it. any way else to access it?
I couldnt find storage device manager

---

### Post by sohlinux on 2010-11-14
go to desktop menu applications ubuntu software center then search for Pysdm and install it, then you can access it from desktop menu under system - administraion - storage device manager

---

### Post by moo9801 on 2010-11-14
k i'm on it!  ETA: 15 minutes. Silly IDE drive is sloooooooooww

---

### Post by moo9801 on 2010-11-16
Ok i finally gave up and reinstalled, but now on boot, i just get a blinking cursor in left hand  corner.  Boot order is correct, i can't think of anything...
EDIT: LOL FAIL! i misread and didn't install a boot loader :P my ubuntu server is now under control!

sohlinux, thank you for everything!  You are on my list of MVP's now, trust me.

---

### Post by sohlinux on 2010-11-17
> **moo9801 said:**
> Ok i finally gave up and reinstalled, but now on boot, i just get a blinking cursor in left hand  corner.  Boot order is correct, i can't think of anything...
EDIT: LOL FAIL! i misread and didn't install a boot loader :P my ubuntu server is now under control!

sohlinux, thank you for everything!  You are on my list of MVP's now, trust me.

glad to hear it :)

---

