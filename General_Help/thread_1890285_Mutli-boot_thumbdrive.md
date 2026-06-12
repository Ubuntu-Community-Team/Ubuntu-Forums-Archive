---
title: "Mutli-boot thumbdrive"
date: 2011-12-03
forum: General Help
---

### Post by jaimeaux on 2011-12-03
Alright... Need help creating a multi-boot thumbdrive.
 
I've tried several different measures, including:
 

[LIST]
[*]Xboot -- Close but no cigar. Got most OS'es working, but Slackware and Hiren's aren't doing right.
[*]YUMI -- Not at all. Barely had a chance.
[*]Sardu -- wouldn't even start the program.
[/LIST]I'm still considering UNetBootin, but I don't know if that does multiple operating systems. Any input would be much obliged.

---

### Post by zero2xiii on 2011-12-03
Hay,

Oka so your question is confusing for me, but I might be able to nudge you in the correct direction.

Firstly I advise you to make seperate partitions for every OS to be run (just like you would on a normal HDD), then install each one as you normaly would. (Im guessing you get this far). Now as for setting up multi boot I would STRONGLY suggest sticking to GRUB or GRUB2. But define the drives as UUID and NOT the standart /dev/sda etc notation.

If you ask a more specific question, we might be able to help you beter.

Cherz

---

### Post by deonis on 2011-12-03
I was thinking about this also but end up buying a small microSD card reader (1$ on ebay) and a bunch of sd cards (4-6$ for 2g).

---

### Post by jaimeaux on 2011-12-03
I'm not sure how to make that more specific.. but here goes anyway!
 
I just bought a 32Gb Thumbdrive, and I want to boot different Operating Systems off of it, including:
 
Slackware
Backtrack 5
Windows 7
Hiren's boot CD
Ultimate Boot Cd
Trinity Rescue Kit
Ubuntu
DSL
Dr.Web Anti-virus
 
And, System Rescue CD
 
 
I'd like to make the Ubuntu boot a persistent one, if possible.
 
Does that help?

---

### Post by viperdvman on 2011-12-03
Windows 7 alone is gonna take up about half of that USB drive space, easily *(my EeePC's restore partition is that big)*. The rest, however, depends on the LiveCD/DVD iso.

---

### Post by jaimeaux on 2011-12-04
> **viperdvman said:**
> Windows 7 alone is gonna take up about half of that USB drive space, easily *(my EeePC's restore partition is that big)*. The rest, however, depends on the LiveCD/DVD iso.
 
I'm not too worried about windows 7, or even the amount of space it needs. Actually, that one is really just a windows 7 disk that is an installer/recovery disk, so it's just another repair utility for me.

---

### Post by zero2xiii on 2011-12-04
Hay,

This is somewhat complex, but here might be a helping hand:
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

Further in the same direction with more details:
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

This however uses ISO files (I suggest this, as creating 10 partitions in a 32GB drive might be problamatic (seeing as some formats have a 2 - 10% reserved space etc etc etc)..

Dumping 10 Iso files on there and having a single boot loader will be best. Making it persistent? Hmm, have a look at:
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Here is a nice tut, easy to follow without all the techinal jargon that might get you confused:
[http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive](http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive)


If you need more specific help, fitted to your needs. I might be able to help you following those tutorials substituting your systems vars for the correct ones above. But you should be able to follow them real easy if you have some experience with ubuntu.

Good luck
Cherz

---

### Post by jaimeaux on 2011-12-04
Hey, thanks for all the replies!
 
I'll try that, zero2xiii, and get back to you guys on the status. Thanks!

---

### Post by oldfred on 2011-12-04
With 32GB, you have room for a full install of Ubuntu and many ISOs.

Used a 8GB partition for a full install of Ubuntu and used another 8GB for data which I used for several ISOs, but mostly other data. (no swap since I have 4GB RAM).

I have several 4GB flash drives that I have filled with ISOs for recovery/repair ISOs and use grub2 to boot. I did this before some of the scripts that zero2xiii refers to and have a few more links to scripts.

I also wanted to see if I could from Ubuntu create a Windows 7 repairUSB. I did not get a direct install to work, but created a Windows repair CD, used CD to install/copy to a 2GB flash. I found it used so little space and wanted to see if I still could use grub2 to boot it & it worked.:) But you have to be careful that grub2's /boot & Windows /Boot are the same (change one or the other and consolidate files). I then was able to add several repair ISO to the remaining space in another partition and boot with grub2.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

With grub2 persistent C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistent 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)
Full install of 11.04 to USB device C.S.Cameron post
[http://ubuntuforums.org/showthread.php?t=1824194](http://ubuntuforums.org/showthread.php?t=1824194)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

The issue is finding the correct boot stanza parameters for a grub2 boot stanza. I cheat and use some of the scripts versions by reviewing script or find others that have been posted. Sometimes you can open ISO and see what parameters it uses. Not all ISOs can be loopmounted with grub. I in effect had to install Puppy.

More examples:
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by jaimeaux on 2011-12-05
oldfred,
 
 
    Holy crap. That's a LOT of references. I haven't even had a chance to try zero2xiii's, but I think this or more what I'm looking for. Once again, thanks for all the replies everybody!
 
I'll post about the results as soon as possible!

---

### Post by davidecosta on 2011-12-06
Hello.
I'm the developper of SARDU.
Try last beta version for build your pen drive and let me know

---

### Post by jaimeaux on 2011-12-06
Sardu, eh? I can give it a shot. I couldn't really get it to run though...

---

### Post by beew on 2011-12-06
You didn't say which OS you use. If you are using Ubuntu the easiest way to make a multi-boot usb would be multisystem
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Use installation method 1. After running the install script it will add a repository to your sources list and you will get regular updates through the package manager.
The page is in French but the application is actually in English (I guess it depends on where you download).

I am not aware that unetbootin can make multiboot usb.

**EDITED** With a 32G drive you can actually make a few full installations that multiboot instead of making live usb. The speed may be a problem though.

---

### Post by jaimeaux on 2011-12-06
Oh, you're right, I didn't... I have a Windows-7 Box and an Ubuntu box, both at my disposal....

---

### Post by C.S.Cameron on 2011-12-06
MultiBootUSB see:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Windows 7 extract the iso or copy the disk contents to a NTFS partition on the flash drive.

---

### Post by jaimeaux on 2011-12-06
Okay... solution did not work very well. Trying YUMI (updated... issue may have been caused by old version)... and Sardu 2.0.3
 
Will post status.

---

### Post by davidecosta on 2011-12-06
Let me know if works with last beta. In my tests works fine.
If don't works i fix it. I'm releasing new stable version :)

---

### Post by jaimeaux on 2011-12-06
Sardu worked pretty well... I'm short a few of the OS'es, but most of them work. I can't get HBCD (Hirens 14.0) to show up, nor windows 7 install disk....
 
right now I've got it w/ DSL, Ubuntu, Backtrack, System Rescue, Trinity Rescue, Dr Web AntiVir.... looking good so far.

---

### Post by davidecosta on 2011-12-06
For hiren's is my error, fix for next version.
You can fix manually:
Open \SARDU\utility.cfg and change it As you see in the code
 
```

#boot di Hiren's
label Avvio di Hiren's Boot CD
menu label Avvio di ^Hiren's Boot CD
MENU INDENT 1
      #kernel /boot/grub.exe --config-file="configfile /HBCD/menu.lst
      kernel menu.c32
      APPEND /HBCD/isolinux.cfg
 

```

Seven mmmmm in my test works very fine. You have a modified version? Your boot/install.wim is largest of 4 gb? (Limit of FAT32)

---

### Post by jaimeaux on 2011-12-06
> **davidecosta said:**
> Seven mmmmm in my test works very fine. You have a modified version? Your boot/install.wim is largest of 4 gb? (Limit of FAT32)
 
If you're asking if my Windows 7 install is =< 4GB, then yes.

---

### Post by xyzzyman on 2011-12-07
I just recently did this using MultiSystem [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/). I set up multiple 10gb partitions on my hdd and was trying out various flavors of linux, and was just leaving the SD card in its slot for when I wanted to install something new, or f'd up Grub2 and had to chroot and reinstall. 

I've now settled on Ubuntu as my main OS, Arch as secondary, and a Windows for when I want to play games. In Ubuntu I have a Windows 7 Started Edition install just for Netflix in VirtualBox, but I set up VirtualBox to load up my Arch partition and I am finding I use it more and more in full screen to the point that when I shutdown I wind up back in Ubuntu. lol

---

### Post by zero2xiii on 2011-12-07
> **jaimeaux said:**
> If you're asking if my Windows 7 install is =< 4GB, then yes.

Yes somewhat. He has a point. The limitation of FAT32 is no single file can be over 4gb in size. Say for example a DVD iso is 4.7gb or 6.5gb, neither of them will copy to a fat32 formated drive.

NTFS is a #### to get USB booting to work. I have tried that before. Didn't succeed (didn't put in days of my time just to get one ISO to boot either.)

Hope you are getting success. Will really like to hear if it works for you.

If recovery is all that you are intrested in, have a look at:
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) 

There is a more complete one availible on torrent sites which has more OS's to choose from. I am not posting a link to that, since I have no idea what forum policy is governing the posting of torrent links.

Cherz

---

### Post by davidecosta on 2011-12-07
You can tell me about your problems with install of windows7?
Fix hiren's?

---

### Post by jaimeaux on 2011-12-09
I'm confused on how Hirens is supposed to be added on YUMI.. it has it listed as a zip. 

on Sardu, (great program, btw. Good work!) I was able to get it working, but it didn't mount the HBCD tools, so I had to do that part manually.... 

any suggestions?

---

### Post by davidecosta on 2011-12-09
For SARDU i release a new version or today or tomorrow with this fix

---

