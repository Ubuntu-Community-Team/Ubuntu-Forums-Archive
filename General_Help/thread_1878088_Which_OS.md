---
title: "Which OS?"
date: 2011-11-09
forum: General Help
---

### Post by iHoodStar21 on 2011-11-09
I need helping chosing an OS for an old laptop. I will only be using it for browsing forums and using it with Photoshop CS3. Here are the specs. I succesfully run Photoshop on here with no trouble. But want a smaller OS. So that I can have it run faster. Upgrading this laptop isn't an option lol.

Game Booster Diagnose Report v1.0
Version: 3.1.0.1336
Date: 2011/11/09 05:40:02

----------------------------------
01 - Operating System
----------------------------------

0101 - Operating System         : Windows XP Professional (5.1, Build 2600) SP3
0102 - Language                 : English (Regional Setting: English)
0103 - BIOS                     : Phoenix ROM BIOS PLUS Version 1.10 A10
0104 - Processor                : Intel(R) Celeron(R) M processor         1.40GHz
0105 - Memory                   : 504MB RAM
0107 - Page File                : 120MB used, 1108MB available
0108 - Windows Dir              : C:\WINDOWS
0109 - DirectX Version          : DirectX 9.0c (4.09.0000.0904)
0110 - DX Setup Parameters      : Not found
0114 - DxDiag Version           : 5.03.2600.5512

----------------------------------
02 - Processor
----------------------------------

0201 - Caption                  : Intel(R) Celeron(R) M processor         1.40GHz ~1396MHz
0202 - Current Clock Speed      : 1396MHz

----------------------------------
03 - Video Adapter
----------------------------------

0305 - Device Key               : Enum\
0306 - Display Memory           : n/a
0307 - AdapterRAM               : 0
0308 - Current Mode             : 1024 x 768 (32 bit) (1Hz)
0310 - Driver Name              : vga.dll
0311 - Driver Version           : 5.01.2600.0000
0312 - Driver Language          : English
0313 - DDI Version              : unknown
0315 - Driver Beta              : False
0316 - Driver Debug             : False
0317 - Driver Date              : 4/14/2008 05:00:00
0318 - Driver Size              : 9344
0319 - VDD                      : n/a
0320 - Mini VDD                 : vga.sys
0321 - Mini VDD Date            : 4/14/2008 05:00:00
0322 - Mini VDD Size            : 20992
0323 - Device Identifier        : {D7B70EE0-4340-11CF-B063-282AAEC2C835}
0324 - Vendor ID                : 0x0000
0325 - Device ID                : 0x0000
0326 - SubSys ID                : 0x00000000
0327 - Revision ID              : 0x0000
0334 - DDraw Status             : Not Available
0335 - D3D Status               : Not Available
0336 - AGP Status               : Not Available
0337 - Notes                    : The system is using the generic video driver.  Please install video driver provided by the hardware manufacturer.
                                  To test DirectDraw functionality, click the "Test DirectDraw" button above.
                                  Direct3D functionality not available.  You should verify that the driver is a final version from the hardware manufacturer.

0338 - OpenGL                   : 5.1.2600.5512 (xpsp.080413-0845)

----------------------------------
04 - Memory
----------------------------------

0401 - Total Memory             : 503.37 MB
0402 - Free Memory              : 346.46 MB
0403 - Total Pagefile           : 1.20 GB
0404 - Free Pagefile            : 1.08 GB

0405 - Bank Label               : N/A
0406 - Speed                    : 533 MHz
0407 - Total Width              : 64 Bits
0408 - Capacity                 : 512.00 MB

----------------------------------
05 - Network
----------------------------------

----------------------------------
06 - Motherboard
----------------------------------

0601 - Model                    : 0GD366
0602 - Manufacturer             : Dell Inc.

----------------------------------
07 - Sound Device
----------------------------------

0702 - Default Sound Playback   : False
0703 - Default Voice Playback   : False
0714 - Min/Max Sample Rate      : 5063670, 5063670
0715 - Static/Strm HW Mix Bufs  : 5063670, 5063670
0716 - Static/Strm HW 3D Bufs   : 5063670, 5063670
0717 - HW Memory                : 5063678
0718 - Voice Management         : False
0719 - EAX(tm) 2.0 Listen/Src   : False, False
0720 - I3DL2(tm) Listen/Src     : False, False
0721 - Notes                    : No sound card was found.  If one is expected, you should install a sound driver provided by the hardware manufacturer.


----------------------------------
08 - Hard Disk
----------------------------------

0801 - Model                    : ST9408114A(Seagate, 408G)
0802 - Media Type               : Fixed    hard disk media
0803 - Size                     : 37.26 GB
0804 - Interface Type           : Parallel ATA

0801 - Model                    : SanDisk Cruzer USB Device
0802 - Media Type               : Removable media other than    floppy
0803 - Size                     : 7.45 GB
0805 - Driver Date              : 7-1-2001
0806 - Driver Version           : 5.1.2535.0

0807 - Caption                  : C:\
0808 - Capacity                 : 37.25 GB
0809 - Free Space               : 33.83 GB
0810 - Drive Type               : 3-Fixed
0811 - File System              : NTFS

----------------------------------
End of file - 10344 Bytes

Forgot to mention this was a fresh install. No drivers yet. :p

---

### Post by Matti L on 2011-11-09
Xubuntu and Lubuntu have low system requirements.

---

### Post by iHoodStar21 on 2011-11-09
What's the difference between the two. And does wine work properly with Photoshop?

---

### Post by philinux on 2011-11-09
> **iHoodStar21 said:**
> I need helping chosing an OS for an old laptop. I will only be using it for browsing forums and using it with Photoshop CS3. Here are the specs. I succesfully run Photoshop on here with no trouble. But want a smaller OS. So that I can have it run faster. Upgrading this laptop isn't an option lol.


Photoshop will only run by using Wine. (wine needs to be installed from ubuntu's software centre). Wine can be hit and miss.
[http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6584)

Ubuntu comes with Gimp image editor which you can also install.

---

### Post by Matti L on 2011-11-09
Difference is in desktop environment: Xubuntu uses XFCE and Lubuntu uses LXDE.

---

### Post by claracc on 2011-11-09
Lubuntu 11.04 will work very well in this pc.

You'll have chromium browser as default, but always can install a lighther one (epiphany).

In order to use photoshop, you'll have to install wine or playonlinux and run photoshop inside, or you can try gimp as open source alternative.

---

### Post by philinux on 2011-11-09
> **iHoodStar21 said:**
>  And does wine work properly with Photoshop?

From a Wine forum search.
[http://ubuntuforums.org/search.php?searchid=83989534](http://ubuntuforums.org/search.php?searchid=83989534)

---

### Post by iHoodStar21 on 2011-11-09
Downloading Lubuntu as I type this. Any tips or tweak that I would need or want for Lubuntu?

---

### Post by philinux on 2011-11-09
> **iHoodStar21 said:**
> Downloading Lubuntu as I type this. Any tips or tweak that I would need or want for Lubuntu?

Don't forget the forum search tool. :P
[http://ubuntuforums.org/showthread.php?t=1844755&highlight=lubuntu+stop](http://ubuntuforums.org/showthread.php?t=1844755&highlight=lubuntu+stop)

---

### Post by TBABill on 2011-11-09
Lubuntu probably won't need much to get it going how you like it aside from visual stuff (colors, backgrounds, etc.). It's very light and snappy. And the layout is as close to the appearance of XP as you can get.

---

### Post by Seb71 on 2011-11-09
If you want to run Photoshop on that laptop, your best option is to keep Windows XP.

---

### Post by Jerry N on 2011-11-09
> **Seb71 said:**
> If you want to run Photoshop on that laptop, your best option is to keep Windows XP.

I second that.  Unless your XP is really clogged up, you will probably find that Linux is not appreciably faster and you might actually find CS3 to be slower running in Wine.  If you do decide to make the change, be sure you go through the CS3 deactivation process first.  Otherwise, you might not be able to reactivate it on a new install.  Depending what you do with CS3, GIMP might be an adequate alternative.  If you are working with RAW files, GIMP will truncate them to 8 bits.  GIMP is available for Windows and is free so you could download it and see if it will do what you want to do before making any drastic changes.  

Jerry

---

