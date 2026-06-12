---
title: "Problems burning within Linux"
date: 2006-05-17
forum: General Help
---

### Post by leach on 2006-05-17
Here's a problem I've always had with Linux on every distribution I've ever tried- I've never been able to burn a cd or a dvd. After Burning it always tells me the burn was successful but it's wrong. Linux can't see a disk in the drive, and on the backside of the cd, the line where you can kind of see where it has had data burned on to and where it hasn't starts a half a centimeter away from the center of the disk leaving a ring of unburnt media around the center of the disk. I can't figure out why, but I'm using a Pioneer DVD-RW DVR-105 drive if that rings any bells, maybe there's a problem with linux and Pioneer drives that I don't know about. I realizes this is probably too much information but I can't figure it out. Thanks for any help.

---

### Post by tbresson on 2006-05-17
Could it be as simple as there's a check somewhere that says "test burn" ?

---

### Post by StefanoCole on 2006-05-17
I am wondering if it could be a firmware problem of your burner. You can check if a firmware update is available from the manufacturer for your pioneer burner.

Stefano

---

### Post by bleucanard on 2006-05-17
I had similar problems with a pioneer dvr100. I had to download the latest cdrw tools ([http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-tools-6.1.tar.gz](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/dvd+rw-tools-6.1.tar.gz)) and rebuild them. (here's why : [http://fy.chalmers.se/~appro/linux/DVD+RW/hcn.html](http://fy.chalmers.se/~appro/linux/DVD+RW/hcn.html) , look for Pioneer)

There may be a precompiled package available somewhere (anybody knows ?)

If you need to recompile the source, you will need to apt-get the build-essentials package (and possibly the autoconf, if I remember well). The ubuntu wiki has instructions there :
[https://wiki.ubuntu.com/InstallingCompilers](https://wiki.ubuntu.com/InstallingCompilers)

Uncompress the dvd tools archive in a folder, and in a terminal, in that folder, type make all.
When done, type make install.

To check if it has installed correctly, type growisofs --help, and check that the version is 6.xx

---

### Post by leach on 2006-05-17
I downloaded it and built it but it looks like I already had it installed. I went to the terminal and typed growisofs --help and sure enough it was already there version 6.1, So I'm going to assume that either growisofs isn't configured correctly or I have a diffrent issue.

---

### Post by Gannin on 2006-05-17
Even if you already have the program installed on your computer, you still should compile and install the program yourself.  When you install a precompiled binary package, the program is configured in a very general way.  When you compile a program and install it yourself, it will be optimized and configured for your hardware, because it was built on your hardware.  This gives you the greatest chance of success.

---

### Post by leach on 2006-05-17
Thanks for the advice about building it myself. However, when I try make install, I get  

make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/saint/Desktop/dvd+rw-tools-6.1'
make: *** [install] Error 2

I've never got any errors when compiling before, any remedies?

---

### Post by Gannin on 2006-05-17
After changing into the source's directory in the terminal, you should try something like this.

```

./configure --prefix=/usr
make
make install

```

---

### Post by leach on 2006-05-18
[quote=Gannin]After changing into the source's directory in the terminal, you should try something like this.

```

./configure --prefix=/usr
make
make install

```[/quote] 
I'm afraid that didn't work because you don't use the ./configure command when building it. However after some googling I learned that make install expects two programs to be there so you have to type


```

make btcflash
make rpl8
make install

```

---

### Post by leach on 2006-05-18
It appears that dvd+rw-tools didn't solve my problem, I still get a ring of unburnt media aound the center of the disk. And when I insert it, it is detected as a blank cd.

---

### Post by YuHoo on 2006-05-18
That unburnt area is most likely where the table of contents ought to be, which would explain why it is seen as a blank disk (same thing as a quick erase on a CD-RW). As for your burner, I quickly checked and it does not seem like there are many problems, none like yours. Thus I pose a few questions for you. What burning software are you using? What method are you burning with (tao, dao, etc...)? And what system are you using (Joliet, and others). If I was in your position, I'd grab a cd-rw and start messing with options. 

P.S. I did a light search (by no means thorough) but I did not find linux apps to upgrade firmware, but there are windows apps to upgrade and test the drive. I'd only emulate these as a last resort though, I'd rather install a windows partition and do a quick windows install than attempt something that could screw it up  forever. Better safe than sorry and I don't have the knowledge to give you a definitive answer on if it is safe or actually going to do anything for your problem.

---

### Post by leach on 2006-05-18
The Software I'm using is the built into Banshee 10.10 but I've had the same results with the Nautilus burning program too. I have no Idea if I'm using Disk or Track at once because banshee doesn't give you the option to change it. Before I burnt the CD-R, I burnt a CD-RW (in Banshee) to test dvd+rw-tools and unlike the CD-R it worked fine. I guess I'll try and upgrade it's firmware next, I have a crap-box Dell running windows I keep around to hold extra hardrives and use skype so I guess I could just plug my drive into there and see if upgrading the firmware does any good.

---

### Post by leach on 2006-05-20
Well I just upgraded the firmware and it looks like it did no good.

Edit- My bad, I did something dumb it works now.

---

