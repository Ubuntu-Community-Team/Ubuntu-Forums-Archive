---
title: "Something is wrong with the avaible Live CD ISO Image"
date: 2005-03-11
forum: General Help
---

### Post by MAZDA on 2005-03-11
Hi,

I downloaded the latest Hoary Live CD with the Bittorent Tool Azureus from:
[http://cdimage.ubuntu.com/releases/hoary/array-6/hoary-live-i386.iso](http://cdimage.ubuntu.com/releases/hoary/array-6/hoary-live-i386.iso)

During start up it complains that the CD is corrupted and a CD test fails.

A compersation of the MD5 Checksums between the Original Live CD Image from the ubuntu server and my downloaded  Live CD Image on my Harddisk
don't show any difference.
The MD5 Checksums are the same and it's say all that between the two ISO Images don't exist any difference.

[http://cdimage.ubuntu.com/releases/hoary/array-6/MD5SUMS](http://cdimage.ubuntu.com/releases/hoary/array-6/MD5SUMS)
5bd9def66c81cd201bbe6d5a0d633e10  hoary-live-i386.iso

However.
After that very confused situation i have made also a MD5 Checksum on all files on the Burned Ubuntu Live Cd in compersation with the avaible MD5 Checksum File on the Burned CD and i have found that two Files on the CD are Curupted.

The Currupted Files that don't have the Same MD5 Checksum are

1: 
**\install\netboot\pxelinux.cfg\default**

and 2:
**\install\netboot\pxelinux.0**

After a view in the Preferences of this Files in the opened ISO Image that i have downloaded i have found that ther Lenght is always Zero Bytes long.

It seems me that something must be wrong with the avaible ISO Live Image from the Ubuntu Server.

Can somebady help me.
Is possible that the Live ISO Image on the Ubuntu Server is corrupted ?
What can I do as next.
Where can i download the two Files that are wrong to replace it.

Thank you very much in advance for your answers.
Greetings Mazda.

---

### Post by hkl8324 on 2005-03-11
Do you verify the disc after burning?

anyway, i dont have this problem

---

### Post by MAZDA on 2005-03-11
Hello.

After the reading of the Ubuntu Faq a have found that i have downloaded
the false ISO Image.

[http://www.ubuntuforums.org/showthread.php?t=5608](http://www.ubuntuforums.org/showthread.php?t=5608)
[http://ubuntuguide.org/](http://ubuntuguide.org/)

The right ISO Image is these how contain the Text "live preview" and is about 500 MB big.

The false Image is these how only contain the text "live" and is about 400 MB big.

[http://linuxcompatible.org/story42839.html](http://linuxcompatible.org/story42839.html)

> Ubuntu Hoary Array CD 6 is now available, after a short delay due an outage at their data center:

Array CD 6 is ready. This is the sixth in a series of milestone CD images, released when they're known to be reasonably free of showstopper CD-build or installer bugs, while representing very current snapshots of Hoary. You can download it here:

[http://cdimage.ubuntu.com/releases/hoary/array-6/](http://cdimage.ubuntu.com/releases/hoary/array-6/)


The problem was that i have reading the False Articles on the Web and not the Ubuntu Faq.

Now it Function all  :lol:  :lol: 

Ubuntu is loaded and all my Devices USB, PCMCI Ethernet Card, CD ROM BURNER .... and so on funtion great.
I post even this pices Text under the Operating System 'Ubuntu'.
Great  :lol: 

Thanks a lot for this Great Product   =D>  =D>  =D> 

P.S. The two Files are allways corrupted.
Even in the very well worked hoary-preview-live Iso Image.
But it's seem that this is not such a big problem.

---

### Post by MAZDA on 2005-03-11
[QUOTE=hkl8324]Do you verify the disc after burning?

anyway, i dont have this problem[/QUOTE]

Hello hkl8324.

Thanky you very much for your Answer.

I have downloaded now two LIVE ISO Images 
and the size of the two Files in the Two Images are allways zero Byte big.

Thats easy to compare.

You can also find the corupted Files with the using of this great tool that controll and verify easy the MD5 Hashes of the files.

[http://www.md5summer.org/](http://www.md5summer.org/)

I have installed it under Windows.
After the loading of the MD5 File on the Burned Cd and the veryfing of the MD5 Hashes on the Burned CD it will show you allways that the two files are corrupted on the Live ISO Images.

How ever it's speek all that this is not really a big problem because this files are normaly not used for the Live Session of Ubuntu.

---

### Post by hkl8324 on 2005-03-11
[QUOTE=MAZDA]Hello hkl8324.

Thanky you very much for your Answer.

I have downloaded now two LIVE ISO Images 
and the size of the two Files in the Two Images are allways zero Byte big.

Thats easy to compare.

You can also find the corupted Files with the using of this great tool that controll and verify easy the MD5 Hashes of the files.

[http://www.md5summer.org/](http://www.md5summer.org/)

I have installed it under Windows.
After the loading of the MD5 File on the Burned Cd and the veryfing of the MD5 Hashes on the Burned CD it will show you allways that the two files are corrupted on the Live ISO Images.

How ever it's speek all that this is not really a big problem because this files are normaly not used for the Live Session of Ubuntu.[/QUOTE]


thanks..

but i think i want to inform you is checking md3sum on the bit-torrent-downloaded iso is somewhat rededant, i have read the faq of the official bit-torrent site that the bit-torrent software do that doing the process of download, so you only have the integrity of the burned cd but not the iso image on the HD.

---

### Post by bugmenot on 2005-08-15
**Something really must be wrong with that install-iso!**

I just tried to install ubuntu-5.04-install-i386.iso, 615.307.264 Bytes as **server**. (havn't tried desktop yet since I don't need it).

I failed, because ./install/netboot/pxelinux.0 has a wrong md5 checksum.

The "fsum"-Tool confirms that:

> 
Q:\>fsum -jf -c md5sum.txt

SlavaSoft Optimizing Checksum Utility - fsum 2.51
Implemented using SlavaSoft QuickHash Library <www.slavasoft.com>
Copyright (C) SlavaSoft Inc. 1999-2004. All rights reserved.

NOT FOUND    *****        ./install/netboot/pxelinux.cfg/default
[color=red]FAILED       MD5          ./install/netboot/pxelinux.0[/color]
NOT FOUND    *****        ./pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb

1 checksums failed
2 file errors



Here follows the checksum I get out of pxelinux.0:
> 
; SlavaSoft Optimizing Checksum Utility - fsum 2.51 <www.slavasoft.com>
;
; Generated on 08/16/05 at 00:23:05
;
d41d8cd98f00b204e9800998ecf8427e *pxelinux.0


And this is what md5sum.txt says:
> 
b97f255a7f47a619eeed4faf9dc09dbf

[b]
By the way, I just saw pxelinux.0's filesize is ZERO.
No wonder than.
But it's still the official ISO I downloaded (twice).
[/b]

---

### Post by bugmenot on 2005-08-16
It's me again.

Today I solved my problem.

Although this MD5 checksum on pxelinux.0 seems to be really wrong, my ISO now installs after I used a new CD-ROM drive.

The one which didn't work was an old Mitsumi FX something (maybe 8x), and for sure it had problems with reading the CD-RW.

Nevertheless it's strange that this CD-ROM drive reported the wrong MD5, which obviously was the right action to take?!

---

### Post by beebelo on 2005-08-16
Hi,  and thanks bugmenot for the reference from the other thread.  I guess there are a number of people chasing the same issue around in different threads...
[http://www.ubuntuforums.org/showthread.php?t=37916](http://www.ubuntuforums.org/showthread.php?t=37916)
[http://www.ubuntuforums.org/showthread.php?t=57122](http://www.ubuntuforums.org/showthread.php?t=57122) 

I'm glad you solved your problem, but I'm not so sure you're correct about the solution though ...

My story compared to yours:

I'm using the install iso, not live.

My errors involve the same files as you and others 

I also got a good md5 check on the iso image *before* burning.

I used a fairly new (3 yrs old) burner that I've never had trouble with before.

I burned to a CD-R, whereas you burned to a CD-RW (point being that CD-RWs are more prone to problems)

... so I don't know what to say.  *l*

I've got Ubuntu hoary hedgehog already installed, and it works fine.  I installed that off of the free cds from shipit.  I just thought I'd try Kubuntu as a completely different installation, and downloaded the iso.  

I hope someone knows the answer to this puzzle!

---

### Post by bugmenot on 2005-08-17
beebelo,

if you are not using english as your native language in the installer, give it a try and choose english.
I tried the same before I put in the new CDROM drive, and the pxelinux.0 - error was gone (ok, I got a checksum error on another file then, think it was libelfg.0).

Maybe it works for you without getting another error.

---

### Post by beebelo on 2005-08-17
Darn.  Well I did use English when I installed Ubuntu.  I didn't have time to mess with the Kubuntu iso yet.  I still have to re-burn it.  Anyway, I'm guilty of going off-topic, since my problem is with the install cd.  

Here's something I'm wondering about in general.   Which of the following is the most prone to having errors:  
 - downloading an iso image by http or ftp
 - downloading a bit torrent (I understand that bit torrent is very reliable)
 - transferring an iso from hard drive to a usb flash drive and back to another      hard drive (what I had to do)
 - burning the cd

Anyone care to comment??

---

