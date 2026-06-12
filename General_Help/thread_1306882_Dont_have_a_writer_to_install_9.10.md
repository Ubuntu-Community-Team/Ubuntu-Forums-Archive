---
title: "Dont have a writer to install 9.10"
date: 2009-10-30
forum: General Help
---

### Post by simartem on 2009-10-30
I dont have a DVD burner.. I have the Karmic Koala 9.10 release in **iso format** and i am running Windows XP OS. How can i install this to my empty HDD, drive D ?

---

### Post by P4man on 2009-10-30
Easy, make a bootable USB stick.
Download [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) for windows to create the stick, reboot your PC set your bios to boot from usb and start playing with it :)

---

### Post by simartem on 2009-10-30
i only have a 2 GB stick.. :(
I have an external 1 TB but i dont know if it helps or can i use WUBI ? If yes.. How ?

---

### Post by P4man on 2009-10-30
> **simartem said:**
> i only have a 2 GB stick.. :(
I have an external 1 TB but i dont know if it helps or can i use WUBI ? If yes.. How ?

You only need 650Mb. You use the stick as installation "cd". It boots from the stick into a working ubuntu environment so you can play and test it, if you're ready to install to harddisk just double click the install icon on the desktop.

and yes you could use wubi, but since you got a spare drive to install to you would makes things difficult and messy for no reason. Wubi is useful if for some reason you can not or do not want to change partitions and you only have a single windows partition. If that is not the case, dont use wubi.

---

### Post by simartem on 2009-10-30
I have 2 internal HDD and 1 External (1TB).
 
In HDD(0) is running Windows XP on single partition.
In HDD(1) is empty and clean..
 
What is the latest option for me :) Thank you.. And my ISO file is about 3,87 GB.. I dont know what you mean by 650 MB ? Where would i download this 650 mb file ?

---

### Post by Crash~Override on 2009-10-30
go download unetbootin and get a 1gb or larger usb flash drive. Install the iso to the flash drive using unetbootin and boot from the usb!

---

### Post by simartem on 2009-10-30
Will i download Windows version of unetbootin or linux version ?

---

### Post by P4man on 2009-10-30
> **simartem said:**
> I have 2 internal HDD and 1 External (1TB).
 
In HDD(0) is running Windows XP on single partition.
In HDD(1) is empty and clean..
 
What is the latest option for me :) Thank you.. And my ISO file is about 3,87 GB.. I dont know what you mean by 650 MB ? Where would i download this 650 mb file ?

ah you got the dvd version. wellm tough luck then, download the regular cd version :)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Or use bittorrent if you can:
[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)
> 
Will i download Windows version of unetbootin or linux version ?

Windows since you will be making the live usb stick in windows

---

### Post by simartem on 2009-10-31
I have downloaded both the regular CD version of 9.10 and Unetbootin however my installation hangs at %5 of the process :( Says.. Extracted 9 of 161 files but the led of my USB drive seems still flickering.. I tried with another USB drive but the process still hangs.. Do i have a chance (asking in the name of file size) to burn the regular cd image to a 700 MB CD ?

---

### Post by P4man on 2009-10-31
> **simartem said:**
> I have downloaded both the regular CD version of 9.10 and Unetbootin however my installation hangs at %5 of the process :( Says.. Extracted 9 of 161 files but the led of my USB drive seems still flickering.. I tried with another USB drive but the process still hangs.. Do i have a chance (asking in the name of file size) to burn the regular cd image to a 700 MB CD ?

What "installation" hangs? Creating the USB stick in unetbootin? Perhaps you are just not patient enough, ive never used it but there is a good chance some files are huge other tiny. Another possibility is that your download is corrupt. You can test the integrity of the download with this:
[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows)
Or download ubuntu iso through bittorrent then you are sure of the integrity.

But yes, you can also burn it to a cd of course, but if the iso is corrupt that wont help.  If you need help burning an iso in windows go here:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by P4man on 2009-10-31
BTW if all else fails (but there is no reason it should) you can request a free cd here:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Does take a long time but its free as in free beer.

---

### Post by simartem on 2009-10-31
thank you p4Man.. You're right, i wasnt patient enough, i finally was able to fill the USB Stick with the karmic ISO file and boot was succesfull.. I finally installed the clean 9.10 to my HDD(1).. I think i will have some problem with ATI Radeon onboard graphics adapter.. How can i see if the VGA display driver is correctly installed ?

---

### Post by P4man on 2009-10-31
> **simartem said:**
> thank you p4Man.. You're right, i wasnt patient enough, i finally was able to fill the USB Stick with the karmic ISO file and boot was succesfull.. I finally installed the clean 9.10 to my HDD(1).. I think i will have some problem with ATI Radeon onboard graphics adapter.. How can i see if the VGA display driver is correctly installed ?

If you have a working gui then it cant be all that wrong :)
Which onboard ATI card do you have? If you're not sure, open a terminal in applications > accessories and type 

```
lspci
```
(that is LSPCi in lowercase)

ATI cards prior to the HD2xxx (I think) are no longer supported by ATI's linux drivers, but they are supported by opensource videodrivers which will be installed and used automatically.

---

### Post by simartem on 2009-10-31
I think i need to create a xorg.conf to use fglrx driver ? Is it possible ?

---

### Post by P4man on 2009-10-31
> **simartem said:**
> I think i need to create a xorg.conf to use fglrx driver ? Is it possible ?

what videocard do you have?
Normally the right driver for your card will be loaded automatically, it will not show in xorg. xorg.conf by default is empty these days (though you can still override stuff by putting it in there).

Are you having any issues, or just suffering from the windows syndrome of wanting to install drivers?

---

### Post by simartem on 2009-10-31
compiz refuse to work.. I have ATI RADEON IGP 9100

```

citir@abcd:~$ sudo compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1152x864) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present.

```

---

### Post by P4man on 2009-10-31
there is absolutely no reason to run compiz as root. Dont use sudo when you dont have to, it can mess things up badly.

Go to system > prefences > appearance
visual effets
try setting them to extra.

If that works, and you get wobbly windows, then compiz works.

---

### Post by simartem on 2009-10-31
system > preferences > appearance > visual effects > extra 

fails.. it doesnt work.. I had compiz working in 9.04 before :(

lspci output :

```

00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 17)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 9100 IGP
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:08.0 Ethernet controller: 3Com Corporation 3Com 3C920B-EMB-WNM Integrated Fast Ethernet Controller (rev 40)

```

How can i switch to fglrx for my device ?

---

### Post by P4man on 2009-10-31
you cant use fglrx. Thats the binary ATI driver. The new ones dont support your videocard, the older ones dont support the current version of X.org. That would have been the same in jaunty however,perhaps you downgraded your xorg, but I would strongly advice against doing that in karmic (if its even possible)

Have a look here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by simartem on 2009-10-31
i am not an experienced user in Linux, i dont know how to handle this compiz thing :)
My video-card was sufficient for most of the compiz effects running on 9.04 , but now it doesnt work on 9.10. I dont know what to do now

---

### Post by P4man on 2009-10-31
> **simartem said:**
>  I dont know what to do now

read :)
Just read that article, you dont have to be a linux expert to follow the instructions. If you dont understand sonething just ask. No guarantee it will help, but its worth trying.

---

### Post by simartem on 2009-10-31
appreciate your effort for helping. regards

---

