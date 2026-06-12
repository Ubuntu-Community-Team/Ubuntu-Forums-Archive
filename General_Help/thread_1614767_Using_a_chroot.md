---
title: "Using a chroot"
date: 2010-11-06
forum: General Help
---

### Post by emoguitarist06 on 2010-11-06
I'm running Ubuntu 10.10 64bit and I have succesfully installed 10.10 32bit as a chroot using [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
I'm able to go into the chroot shell and it works perfectly

Now I need to know how to use it lol

I want to run PCSX2. I have it downloaded in my personal Downloads folder but how to I access it from a chroot? also will I have to install all the libs required for PCSX2 within the chroot itself?

I'm lost

any direction whatsoever would help!!

---

### Post by HermanAB on 2010-11-06
Howdy,

Chroot is very last century and a pain in the derrier to use.  You should rather use VMware or Virtualbox.

---

### Post by emoguitarist06 on 2010-11-06
> **HermanAB said:**
> Howdy,

Chroot is very last century and a pain in the derrier to use.  You should rather use VMware or Virtualbox.

What? Are you Sure? I understand virtualization as I run Windows 7 in VirtualBox

According to PCSX2
[http://code.google.com/p/pcsx2/wiki/ChrootAnd64bStatusLinux](http://code.google.com/p/pcsx2/wiki/ChrootAnd64bStatusLinux)
CHROOT is the best route to take which was just updated in September

I am not trying to virtualize an entire operating system and WASTE that much resources just for 1 program

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot) states that one good use of chroot is for Running 32-bit applications on 64-bit systems

---

### Post by emoguitarist06 on 2010-11-09
Bump

---

### Post by Yellow Pasque on 2010-11-09
Did you bind mount your home directory (or whatever other directory) in /etc/fstab?
> also will I have to install all the libs required for PCSX2 within the chroot itself?
Yes. That's the point of the chroot (to use 32-bit libs).

> Chroot is very last century and a pain in the derrier to use. You should rather use VMware or Virtualbox.
LOL. The 3D support/performance provided by the virtualbox driver is nowhere near what one can get with a native chroot. Chroots are not deprecated by VM's.

---

### Post by emoguitarist06 on 2010-11-09
> **Temüjin said:**
> Did you bind mount your home directory (or whatever other directory) in /etc/fstab?
**No but I will tonight and post my results**
I did check
$ sudo editor /etc/schroot/mount-defaults
and made sure nothing was commented (#)

> **Temüjin said:**
> 
Yes. That's the point of the chroot (to use 32-bit libs).
So obviously I'm going to need to add the repos to be able to add the libs.

> **Temüjin said:**
> 
LOL. The 3D support/performance provided by the virtualbox driver is nowhere near what one can get with a native chroot. Chroots are not deprecated by VM's.
That what I thought ;)

---

### Post by emoguitarist06 on 2010-11-09
I mounted my home folder into my chroot using
```
sudo mount -o bind /home /var/chroot/home
```
it worked perfectly

Now how do I add repos? I can't
```
gedit /etc/apt/sources.list
```
because gedit isn't installed

and what repos do I need?
> You need the following installed: libasound2-dev, libbz2-dev, libgl1-mesa-dev, libglew1.5-dev, libglu1-mesa-dev, libgtk2.0-dev, libjpeg-dev, libsdl1.2-dev, libsoundtouch1-dev, libsparsehash-dev, libwxbase2.8-dev, libwxgtk2.8-dev, libx11-dev, nvidia-cg-toolkit, portaudio19-dev, zlib1g-dev

---

### Post by emoguitarist06 on 2010-11-09
I also tried
```
sudo add-apt-repository ppa:gregory-hainaut/pcsx2.official.ppa 
```
but "add-apt-repository" isn't found lol

That's the official PPA noted here
[http://code.google.com/p/pcsx2/wiki/CompilationGuideForLinux](http://code.google.com/p/pcsx2/wiki/CompilationGuideForLinux)

---

### Post by emoguitarist06 on 2010-11-10
**[COLOR="Red"][SIZE="5"]UPDATE[/SIZE][/COLOR]**

I copied all the repos from my friends 32bit Maverick and I installed all libs BUT here is my problem
```
root@phillipguy-laptop:~/Downloads/pcsx2-0.9.7-r3881# ./pcsx2 
Error: Unable to initialize gtk, is DISPLAY set properly?

```

I have tried 
```
export DISPLAY=:0.0
```
as noted here:[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
but still no luck

---

### Post by emoguitarist06 on 2010-11-10
**[COLOR="Blue"]SOLVED[/COLOR]**

Using the knowledge here:
[http://wiki.mandriva.com/en/Development/Howto/Chroot#Launch_X_Applications_inside_the_chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot#Launch_X_Applications_inside_the_chroot)

I installed Xephyr
which in Maverick is:
```
sudo apt-get install xserver-xephyr
```

I mounted /dev/input/ to my chroot so I can use my PS3 Sixaxis controller
*in chroot shell*
```
mkdir /dev/input
```
*outside shell*
```
sudo mount -o bind /dev/input /var/chroot/dev/input
```

Finally to run my graphical application
*outside shell*
```
Xephyr -ac -fullscreen :1
```
You can remove -fullscreen if you don't want fullscreen but for PCSX2 I couldn't play it without -fullscreen
*inside chroot*
```
export DISPLAY=localhost:1
```
and then run your program... in my case ./home/phillipguy/Downloads/pcsx2

---

