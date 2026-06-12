---
title: "Running 2 instances of VLC?"
date: 2010-11-07
forum: General Help
---

### Post by tobytoby on 2010-11-07
I would like to use VLC for both capturing audio line in as well as using VLC to play audio clips that is supposed to be mixed with audio from line in. Can I run 2 instances of VLC at the same time and still be able to control the instances separately via bash scripts?

Thanks in advance/Toby

---

### Post by sikander3786 on 2010-11-07
I think it is under Edit > Preferences. Uncheck the Allow only one instance tick box.

---

### Post by tobytoby on 2010-11-07
It is unchecked already. The error msg I get is "socket error" so it seems it is some kind of collision. (I am a beginner, hence my 'not so specific' descriptions).

---

### Post by tobytoby on 2010-11-07
Bump...

BTW, here is the error ms I get when strarting the 2nd instance of VLC via a bash script==>

VLC media player 1.0.6 Goldeneye
[0x879eb48] main interface: creating httpd
[0x879eb48] main interface error: socket bind error (Åtkomst nekas)
[0x879eb48] main interface error: socket bind error (Åtkomst nekas)
[0x879eb48] main interface error: cannot create socket(s) for HTTP host
[0x879eb48] http interface error: cannot listen on :8889
[0x879eb48] main interface error: no suitable interface module
[0x86fa668] main libvlc error: interface "http,none" initialization failed
[0x86fa668] main libvlc: Kör vlc med standardgränssnittet. Använd "cvlc" för att använda vlc utan gränssnitt.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/user1/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[0x8a36d30] pulse audio output: No. of Audio Channels: 2

---

