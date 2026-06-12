---
title: "What architecture ?"
date: 2010-05-09
forum: General Help
---

### Post by ma$$ter on 2010-05-09
hi
I was trying to install some package on my 10.04 lucid box and I got an error:

[COLOR="Red"]Install failed : 
dpkg: error processing /tmp/.webmin/HandBrake-0.9.4-Ubuntu_GUI_i686.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 /tmp/.webmin/HandBrake-0.9.4-Ubuntu_GUI_i686.deb[/COLOR]

wtf?

I issued an uname -a command:

[COLOR="Blue"]root@xxxxx:~# uname -a
Linux xxxxx 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux[/COLOR]

so I have a i386 installation...

I don't understand why that error ?
please help.

---

### Post by howefield on 2010-05-09
Try downloading and installing the 64 bit version to match your 64 bit operating system.

---

### Post by The Real Dave on 2010-05-09
You need to get the 64bit version of the package, as you are running 64bit Ubuntu. [Here]("http://handbrake.fr/rotation.php?file=HandBrake-0.9.4-Ubuntu_GUI_x86_64.deb") it is I believe.

---

### Post by ma$$ter on 2010-05-10
thank you. I will do that.

but still baffled about **[COLOR="Red"]amd64[/COLOR]**.
is it AMD processor related ?
because my CPU is an Intel Dual Core...

---

### Post by wojox on 2010-05-10
> **ma$$ter said:**
> 

I issued an uname -a command:

[COLOR="Blue"]root@xxxxx:~# uname -a
Linux xxxxx 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux[/COLOR]

so I have a i386 installation...


You don't have 32 bit processor you have a 64 bit (x86_64) and you installed Ubuntu 64 bit.

---

### Post by prodigy_ on 2010-05-10
> **ma$$ter said:**
> amd64
AMD was the first to introduce x86-64 extensions of the x86 instruction set. Their implementation was called AMD64 and among package builders it's still quite common to use this nickname when referring to x86-64 capable systems.

---

### Post by howefield on 2010-05-10
> **ma$$ter said:**
> but still baffled about **[COLOR="Red"]amd64[/COLOR]**.

The term AMD64 goes back to when only AMD had a 64 bit processor, so the name stuck even after Intel caught up.

---

### Post by JohnAStebbins on 2010-05-10
HandBrake 0.9.4 will not work on ubuntu 10.04.  You need to use the nightly snapshot.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

