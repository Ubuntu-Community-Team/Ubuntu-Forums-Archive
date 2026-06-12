---
title: "Unable to play DVD with Ubuntu 10.04"
date: 2010-06-29
forum: General Help
---

### Post by sastusbulbas on 2010-06-29
Hi all,

When I put a DVD in my DVD drive I cannot get Ubuntu to play it, not with VLC, Enna, Boxee or Movie Player, with movie player I get "An Error Occurred Could not open location; you might not have permission to open the file."

With VLC I get some very slow jerky playback that crashes when I go full screen.

---

### Post by Anton32828 on 2010-06-29
Did DVDs play on that computer under a previous version of Ubuntu?
 
I get the same error with my netbook (HP Mini110 with USB DVD drive) due to what I assume are limitations of the hardware. Some DVDs would barely play under 9.10 but most would not. So getting a new error under 10.4 was interesting but not surprising in that case.
 
On my more powerful machines (desktop, work laptop) 10.4 plays DVDs very well.

---

### Post by stoneage on 2010-06-29
Try launching the application from a Terminal and post whatever errors are displayed when you try the DVD.

It could be you don't have libdvdcss, or libdvdread installed.

---

### Post by Spr0k3t on 2010-06-29
To quote the information from [Medibuntu.org]("http://www.medibuntu.org"):

> Medibuntu's repository is deactivated by upgrading to a newer Ubuntu release, so you should run this command again after the release upgrade.

Back to the OP.  Try opening the VOB file through VLC directly and post back what you find.

---

### Post by sastusbulbas on 2010-06-29
Hi,

This is the PC's spec

Asrock 4CoreDual Sata II motherboard
Intel E5200 @2.5GHz per core cpu
Silverstone NT01 passive cpu cooler
Corsair XMS Pro PC-3500LL 2x1gb memory
HIS IceQ Pro Turbo HD3850 512mb AGP graphics
M-Audio 24/96 sound card
Asus PCI wireless card
Samsung 640gb F1 hard drive
Samsung IDE DVD drive
Corsair 450w modular psu
Silverstone Lascala LC13 PC case with Sharkoon Silent Eagle SE 80mm fans

Now running Ubuntu 10.04 32bit os

This machine was put together to evaluate W7 Ultimate release candidate which recently expired. This played DVD and 1080 movie files and flac and WAV music files streamed from my downstairs PC via wireless network connection into a projector and audio system upstairs. It worked very well with only the Wireless card being a bit fussy due to it being one aerial and at an odd location.

---

### Post by jmszr on 2010-06-29
sastusbulbas,

To play DVD's:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) , and/or 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) .  libdvdread4 and libdvdcss2 should be installed.

---

### Post by sastusbulbas on 2010-06-30
Been through all that and have libdvdcss - libdvdread installed?

About the closest I get is VLC with it's poor picture quality and jerky frame rate which crashes on full screen.

This is with a DVD in the DVD drive as I seem unable to get a proper streaming connection with Ubuntu and my PC

---

### Post by Clever_Username on 2010-06-30
Did you try launching it from a terminal like Stoneage suggested?

---

### Post by sastusbulbas on 2010-06-30
Launching from terminal does not seem to sort out playback, but this is what terminal shows. I should also add that this system becomes as responsive as an old Athlon 1800 PC with 128mb of Sdram running XP Pro while doing a virus scan (well maybe an exaggeration but it certainly slows down and such)

steve@steve-desktop:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x8725148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: POLAR_EXPRESS_DISC_1
libdvdnav: DVD Serial Number: 32EF9B08
libdvdnav: DVD Title (Alternative): POLAR_EXPRESS_DISC_1
libdvdnav: Unable to find map file '/home/steve/.dvdnav/POLAR_EXPRESS_DISC_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00e50000. Regions: 2 4 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000120
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000007ab
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00009593
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00252ede
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00252fbc
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[0xb7401020] main input error: ES_OUT_RESET_PCR called
[0xb7401020] main input error: ES_OUT_RESET_PCR called
[0x8beaee8] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x8ca0050] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xb7401020] main input error: ES_OUT_RESET_PCR called
[0xb74243f8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0xb74243f8] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0xb7401020] main input error: ES_OUT_RESET_PCR called
[0x8be6550] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[0x8ca0050] pulse audio output: No. of Audio Channels: 6
[0x8bdfa80] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000
[0x8ca0050] pulse audio output: No. of Audio Channels:

---

### Post by stoneage on 2010-06-30
What drivers are you using for that card?

Have a look at this:-
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)




EDIT - [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1444494](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1444494)

---

### Post by sastusbulbas on 2010-06-30
When I installed this I looked at the hardware drivers and clicked on the propriety FGLRX graphics driver?

steve@steve-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850 AGP
OpenGL version string: 3.2.9756 Compatibility Profile Context

---

### Post by sastusbulbas on 2010-07-11
OK I have installed Mint 9,04 64bit as dual boot, though currently having wireless problems which means  whole lot of other work as I apparently have to sort out a wired connection to install drivers.

Due to the lack of internet on that side of this HDD I can't try out Boxee, Enna or XBMC.

What is interesting is that it plays DVD's fine with VLC and Gnome player where my Ubuntu install does not?

---

### Post by stoneage on 2010-07-11
I think Mint ships with some codecs that Ubuntu doesn't, so that could be the difference.

As for the wireless, I am not up to date with it, but I read that a kernel update broke it, so if you are using 2.6.17-11 rolling back to  2.6.17-10 might help.

---

### Post by sastusbulbas on 2010-07-11
Bouncing between them both at the moment, found that updating to the alternative ATI driver left Mint with the same DVD issues I found with Ubuntu?

Clearly some driver issues, system slows down, unresponsive, jerky playback etc.

I have re-installed Mint, as disabling the installed driver didn't help. I guess I will have to try and deduce what Mint drivers and codecs are doing what I want, then install the appropriate drivers under Ubuntu?

I am about to download another Ubuntu ISO as my 32bit and 64bit 10.4 versions show an error during the live CD install, even though both seem to work?

---

