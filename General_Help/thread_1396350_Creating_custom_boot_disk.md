---
title: "Creating custom boot disk"
date: 2010-02-01
forum: General Help
---

### Post by worx101 on 2010-02-01
Hello,

We have a project we are working on and wanted to know if it is possible using the ubuntu(or any linux) boot disk.

We need the disk to first wipe the hard disk in the notebook, then perform a hardware test(testing processor/hdd/ram/display)  then it should reimage the machine and reboot from the HDD.

I am thinking of using grub4dos to boot(and timeout to the HDD)

and partiton image to image the HDD... but i do not know any cli software for the others...

For note the disk has to be completely automated as we don't have the headcount to recheck every machine every few minutes.

---

### Post by Ordes on 2010-02-02
mhm.. not quite sure if i get this right...

1. wipe the hard disk
2. perform hardware test (hdd, ram, processor, display)
3. reimage (with what? the OS that was on before? or a fresh one?)
4. reboot from HDD

>> 1-4 should run complete automated ? 

>> if you want this complete automated you gonna have to do some coding ^^

---

### Post by worx101 on 2010-02-03
Was hoping to be able to do it with CLI based software and a shell script :(

(i could do it with dos, but just wanted a better imaging software than Ghost 2003)

---

### Post by Lars Noodén on 2010-02-03
If you want to pimp out an existing install CD, then look at **preseed**
It is a configuration file which is read by the install CD.  It can be *on* the install cd or loaded over the net.  There are almost limitless tricks that can be done with preseed, including setting up an ssh server with key-based authentication and doing install over the net.  (Someone still has to boot the machine to get that going for you though)

Here are [s]two[/s] three examples:
[http://www.debian-administration.org/articles/394](http://www.debian-administration.org/articles/394)
[http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5](http://www.debuntu.org/how-to-unattended-ubuntu-network-install-preseed-p5)
[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

If you are building your own custom install cd, then I would recommend loading the preseed over the net while figuring out what you want to do and how to do it.  Set up nginx, apache or some other service to serve up your preseed image.  Burn a CD-RW with an install image configured to get the preseed via the net.  That way you don't have to re-burn the CD-RW each time you make a change to the preseed file.  

[aptoncd](https://wiki.ubuntu.com/APTonCD) can help, too.  

Some of your cusomizations can be rolled up as a package.  Other customizations can take place in the pre-install or post-install scripts on the install cd.

---

### Post by Lars Noodén on 2010-02-03
As a postscript, don't worry too much about imaging per se.  The fastest way is usually to wipe the partitions and re-install the system and applications and customizations.

If you're managing images for a large cluster of machines, then maybe something fancy like [radmind](http://rsug.itd.umich.edu/software/radmind/) is in order.  Use the CD to create a bare-bones base image and then radmind to keep it clean.

---

### Post by worx101 on 2010-02-03
Need the imaging for other OSes other than Ubuntu tho

---

### Post by bakegoodz on 2010-02-03
I've created a script for wiping and checking hard drives. I don't have it with me now, but I give it to you if you want.

---

### Post by Lars Noodén on 2010-02-03
> **worx101 said:**
> Need the imaging for other OSes other than Ubuntu tho

All of the [suggestions above](http://ubuntuforums.org/showpost.php?p=8767688&postcount=4), namely preseed, aptoncd, and radmind work on multiple systems.  preseed and aptoncd work for any APT-based distro.  For RPM-based distros, you can look at Kickstart.  Kickstart works for Ubuntu, too, but is IMHO more limited than preseed and very hard to debug.  

Radmind works on and with very many different systems.

---

