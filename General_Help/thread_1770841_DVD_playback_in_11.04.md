---
title: "DVD playback in 11.04"
date: 2011-05-29
forum: General Help
---

### Post by the wolfe on 2011-05-29
I just upgraded to 11.04 today, and despite all my other issues with it, have been able to fix the issues, other than the DVD playback. 
in the past I used 
```
sudo apt-get install libdvdread4
```
followed by ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```, but that did not work this time, and yes, I did reboot it to be sure. 

is there a new code to get dvd playback?

---

### Post by hwttdz on 2011-05-29
What's the output of say "vlc dvd:///dev/dvd"?

---

### Post by linuxinstalledfromhdd on 2011-05-29
Here is a walkthrough.. Did you enable Medibuntu repo yet?

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Follow that step-by-step after each fresh installation and you can't go wrong. :)

---

### Post by the wolfe on 2011-05-29
```
wolfe@ubuntu:~$ vlc dvd:///dev/dvd
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x7d7120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1306873894)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3596): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: RESIDENT_EVIL
libdvdnav: DVD Serial Number: 2CCDB65D
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/wolfe/.dvdnav/RESIDENT_EVIL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000200
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00002680
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000026a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0006b1e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0008e985
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002bbc40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002bbc60
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002c6cc0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002c6ce0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002d2040
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002d2060
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002db780
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002db7a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x002e2320
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002e2340
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x002e9880
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x002e98a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x002f3e80
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x002f3ea0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x002f8c20
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x002f8c40
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x00309020
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x00309040
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_0.VOB at 0x00333440
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_12_1.VOB at 0x00333460
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_13_0.VOB at 0x00342ce0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_13_1.VOB at 0x00342d00
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_0.VOB at 0x003517a0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003517c0
libdvdread: Elapsed time 0
libdvdread: Found 14 VTS's
libdvdread: Elapsed time 2
Warning: call to srand(342143)
[0x7f5588001020] signals interface error: signal 17 overriden (0x7f558c404450)
[0x7f5588001020] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]

```
its playing through VLC. Im trying to get it to play through movieplayer.

---

### Post by linuxinstalledfromhdd on 2011-05-29
You have the configured completely different than the walkthrough, so I don't know.

---

### Post by the wolfe on 2011-05-29
i did follow your guide there. It didnt work. Installed, if you would have read, the programs that it says to, and set region to 1 for USA, and movieplayer still says that it needs a plugin to play DVD.

---

### Post by the wolfe on 2011-05-30
anyone have any ideas?

---

