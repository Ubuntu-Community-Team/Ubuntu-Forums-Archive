---
title: "Help! DVD crashes media players"
date: 2009-11-30
forum: General Help
---

### Post by neoh on 2009-11-30
Hi everyone,

Wondering if you can lend a hand: I upgraded to 9.10 from 9.04 about a month back and just found out I can't play DVDs anymore. VLC and Totem both crash when I try to play (no error window, the program just immediately closes).

Never had a problem with DVD playing before..

Tried using the fixes:
[LIST]
[*][https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[*]installed libdvdread3 
[*]installed medibuntu
[*]installed libavcodec52
[/LIST]

But alas, nothing seems to work. Below is the error info:

```

kay@bessie-desktop:~$ cvlc -v dvd://
VLC media player 1.0.2 Goldeneye
[0x9286548] main demux warning: no access_demux module matching "file" could be loaded
[0x929ba98] main interface error: no interface module matched "globalhotkeys,none"
[0x929ba98] main interface error: no suitable interface module
[0x91f1140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x929bad8] dummy interface: using the dummy interface module...
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: ELIZABTH
libdvdnav: DVD Serial Number: 26864995
libdvdnav: DVD Title (Alternative): ELIZABTH
libdvdnav: Unable to find map file '/home/kay/.dvdnav/ELIZABTH.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000140
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000212
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000022a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00000245
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000024a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00096501
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000a2e9a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x0037d75d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x0037d762
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x0037e70b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0037e710
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0037f218
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0037f21d
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted
```

If anybody can lend a hand, I'd much appreciate it.

Thanks!

---

### Post by JBAlaska on 2009-11-30
```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by neoh on 2009-11-30
Thanks for your reply.. Just tried both commands (and installed the medibuntu update along with it) but no dice :(

---

### Post by JBAlaska on 2009-11-30
Try playing it with Totem instead of VLC and see if that works, I have no idea why VLC won't work though, unless your trying to play a Region that's not supported

See this: [Setting DVD Region Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by sojournerC on 2009-11-30
same problem here. DVD's were working for me in VLC and MoviePlayer but stopped working after one of the updates. don't know which.

---

### Post by think13 on 2009-12-13
I've got the exact same problem in 9.10-can't play an Invader Zim DVD :(

```
totem /media/cdrom0
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/david/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000138
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000015c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000160
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000805a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00008d71
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
totem: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted

```

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
> **JBAlaska said:**
> ```
sudo apt-get install ubuntu-restricted-extras
sudo /usr/share/doc/libdvdread4/install-css.sh
```

You may have to reboot after doing this. Also what was the output of the latter command? Should be ```
Killmandline:$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for sin: 
--2009-12-13 20:27:46--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb
Resolving packages.medibuntu.org... 87.98.138.11, 88.191.82.11
Connecting to packages.medibuntu.org|87.98.138.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 37252 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-Vl2akP/libdvdcss.deb'

100%[======================================>] 37,252      88.8K/s   in 0.4s    

2009-12-13 20:27:47 (88.8 KB/s) - `/tmp/dvdcss-Vl2akP/libdvdcss.deb' saved [37252/37252]
```
Unfortunately if you have all the latest updates this will downgrade the libdvdcss and the newer version is better. Might want to try ```
sudo apt-get update
sudo apt-get upgrade
and perhaps
sudo apt-get dist-upgrade
``` to see if that gets you the latest versions. If so then install-css.sh will be unneeded.

---

