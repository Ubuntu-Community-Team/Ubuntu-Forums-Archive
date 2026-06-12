---
title: "multi version thumbdrive"
date: 2010-11-17
forum: General Help
---

### Post by romejoe on 2010-11-17
I am looking to install the 32 bit, 64 bit, and, hopefully, the netbook remix versions on a thumbdrive and have persistent changes, and have them all on the same partition. My thinking is so that I can boot off of it on most computers and have the environment that is optimized for that machine(64 bit on 64 bit machine, remix on netbook). Any ideas?

---

### Post by uRock on 2010-11-17
They will work fine as long as they are on different thumb drives. They will not work if they are all on the same drive, unless you actually use the installer and set up a triple boot, which sounds like a nightmare waiting to happen.

---

### Post by romejoe on 2010-11-17
ok thank you I wanted to avoid triple booting but I might give it a try

---

### Post by oldfred on 2010-11-17
I believe you can have one persistant. 

But I have two USBs. One 4GB has my Ubuntu and many repair ISOs. that I boot from grub2. I can save files but not update each.

My 16GB is a full install but I could have also added some of the ISO like I did on the 4GB install.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

older MultiBoot USB with Grub2 (boot directly from iso files)
Is full script, I only used some commands
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
Maverick now only gives combo box on grub location if you use manual install.
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

### Post by C.S.Cameron on 2010-11-17
This should not be a problem,  atleast for 32 and 64 bit.

First install the versions of Ubuntu you want to flashdrive using MultiBootUSB or equivelent.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

(I mention persistence in a few of my replies to this post).

Booting from a Live CD create a new partition on this thumbdrive using gparted and name the partition casper-rw.

Do an Alt F2 and type "gksu nautilus".

Open grub.cfg which is inside the boot folder.

Add " persistent" after quiet splash on each of the menuentries of the versions you want to be persistent..

Save.

This should work ok for shared persistence between 32bit and 64bit. I'm not sure if remix will share too kindly though, but seems worth a try.

---

### Post by dcstar on 2010-11-17
> **C.S.Cameron said:**
> 
............
This should work ok for shared persistence between 32bit and 64bit. I'm not sure if remix will share too kindly though, but seems worth a try.

About the only difference the Netbook Remix has these days is the different desktop that actually only loads on Netbooks with specific video hardware and optimises the system for those screen sizes.

If you boot up a Netbook Remix system on "normal" hardware it seems to be a standard 32-bit Ubuntu system.

---

### Post by romejoe on 2010-12-03
thank you for all the replies! I tried multiboot however it wasn't what I was looking for. I ended up just installing 64bit and netbook side by side and having them share a home folder parition. It works great so far.

---

