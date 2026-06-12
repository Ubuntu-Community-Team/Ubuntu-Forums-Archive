---
title: "Old Eagle"
date: 2012-07-23
forum: General Help
---

### Post by eslavko on 2012-07-23
Hello...
I'm freshman from XP.
I need to install EAGLE. The synaptic doesn't work but from command line invoked *sudo apt-get install eagle* works.

The problem is that this install Eagle 5.12.0 but I had licence for 4.16.r2. How I can got that version worked? (I don't want to pay for upgrade as I like old version)

I have Ubuntu 12.04 /64

I try to install from rpm but i'm to fresh to understand error mesage... here is....

thanks for any help


~/Downloads$ rpm -i eagle-lin-eng-4.16r2-1.i586.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
	/bin/sh is needed by eagle-lin-eng-4.16r2-1.i586
	libX11.so.6 is needed by eagle-lin-eng-4.16r2-1.i586
	libXext.so.6 is needed by eagle-lin-eng-4.16r2-1.i586
	libc.so.6 is needed by eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.0) is needed by eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.1) is needed by eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.1.3) is needed by eagle-lin-eng-4.16r2-1.i586
	libc.so.6(GLIBC_2.2) is needed by eagle-lin-eng-4.16r2-1.i586
	libdl.so.2 is needed by eagle-lin-eng-4.16r2-1.i586
	libdl.so.2(GLIBC_2.0) is needed by eagle-lin-eng-4.16r2-1.i586
	libdl.so.2(GLIBC_2.1) is needed by eagle-lin-eng-4.16r2-1.i586
	libm.so.6 is needed by eagle-lin-eng-4.16r2-1.i586
	libm.so.6(GLIBC_2.0) is needed by eagle-lin-eng-4.16r2-1.i586
slavko@ePodstresnik:~/Downloads$

---

### Post by raja.genupula on 2012-07-23
you have to convert rpm pkg into .deb file .
then you can install it with 
```
sudo dpkg -i filename.deb

```
read this for more info : [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by eslavko on 2012-07-23
hmm got problem with alien...


sudo alien eagle-lin-eng-4.16r2-1.i586.rpm
Warning: Skipping conversion of scripts in package eagle-lin-eng: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
eagle-lin-eng-4.16r2-1.i586.rpm is for architecture i386 ; the package cannot be built on this system

Seems that package is 32 bit. My OS is 64. Is that possible to install at all? 

Slavko.

---

### Post by raja.genupula on 2012-07-24
have you checked in Eagle packages ?  didnt you find a 64-bit one ?

---

### Post by eslavko on 2012-07-24
Hello...

I'm not able to find 64bit version for 4.16.r2. The newest one have 64bit but not that.
So I'm try to start it in wine but doesn't work. Well actualy work but all the icons are like greyed out. it's just in two similar colors and is very hard to se what is on it. - unusable.

Inded it's works in virtualbox winXP instalation, but that's not the way I want to use it.

---

### Post by dino99 on 2012-07-24
Eagle includes a layout editor, schematic editor, and an autorouter.
The following limitations apply to the EAGLE Light Edition:
The usable board area is limited to 100 x 80 mm (4 x 3.2 inches).
Only two signal layers can be used (Top and Bottom).
The schematic editor can only create one sheet.

Use of eagle freeware is limited to non-profit or evaluation purposes. See
/usr/share/doc/eagle/copyright for more information.

That it: Linux only have the "Light Edition", so you still need to use your commercial Eagle, not the linux one.

---

### Post by eslavko on 2012-07-24
I have license buyed years ago for pro. And used it a lot on win. Now just want to switch to new os! (the license buyed is for both systems already)

As I know the program itself is same for all type of license. The difference/restrictions is based on license file.

---

### Post by eslavko on 2012-08-15
Really nobody can't help me?

It's nonsense to run XP in virtualbox just for old eagle. I tryed Wine but all icon's come invisible (space occupied but the image is visible with a lot of imagination what should be here)

Thanks

---

### Post by eslavko on 2012-08-16
Now I got it working with wine 1.5!

I can't run native linux version.

---

### Post by stef222 on 2012-11-02
Dear eslavko,
I just have installed eagle 4 on my ubuntu 12.04 machine.
I have isntalled the rpm with the command
```
rpm -i --nodeps eagle-lin-eng-4.16r2-1.i586.rpm
```After that I have made a link for the executable with
```
ln -s /opt/eagle/bin/eagle /usr/local/bin
```It´s working so far for me...
Maybe you need to install the 32bit libraries...

Stef

---

### Post by eslavko on 2012-11-02
Doesn't work on my system!


slavko@ePodstresnik:~/Downloads$ rpm -i --nodeps eagle-lin-eng-4.16r2-1.i586.rpmrpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: can't create transaction lock on /home/slavko/.rpmdb/.rpm.lock (No such file or directory)

second try...

slavko@ePodstresnik:~/Downloads$ sudo rpm -i --nodeps eagle-lin-eng-4.16r2-1.i586.rpm
[sudo] password for slavko: 
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
./install: 13: ./install: Bad substitution
warning: %post(eagle-lin-eng-4.16r2-1.i586) scriptlet failed, exit status 2
slavko@ePodstresnik:~/Downloads$

---

