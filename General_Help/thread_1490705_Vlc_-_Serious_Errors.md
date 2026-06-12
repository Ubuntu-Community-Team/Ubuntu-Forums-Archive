---
title: "Vlc - Serious Errors"
date: 2010-05-22
forum: General Help
---

### Post by FinalShot on 2010-05-22
I did the following from [here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8611164"), and now when I run a dvd I get these errors.

```
Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.
Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/cdrom0/VIDEO_TS/'. Check the log for details.
Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///media/cdrom0/VIDEO_TS/'. Check the log for details.

```

I just started Vlc via Terminal, and started up the dvd, here is the output.

```
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: SG1_KIOSK_37_D124
libdvdnav: DVD Serial Number: 32a18e39
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/scott/.dvdnav/SG1_KIOSK_37_D124.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000088d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000bc0
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[0x83f87c8] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Invalid title IFO (VTS_01_0.IFO).
[0x83f87c8] dvdread demux error: fatal error in vts ifo
[0x83f87c8] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[0x8459e80] main access error: no access module matched "dvd"
[0xb74022c0] main input error: open of `dvd:///dev/sr0' failed: no access module matched "dvd"

```

---

### Post by ahso4271 on 2010-05-22
uninstall and get all files from the vlc site

my vlc plays about every format

---

### Post by jamesisin on 2010-05-22
Uh, did you install VLC through Synaptic?  I'm not sure why ahso4271 is recommending to get the files from "their site".  You should be loading your software through Synaptic.

---

### Post by kelvin spratt on 2010-05-22
Their are some DVDs that just won't play due to copyright protection not many but a few.
Have you tried any other DVDs have you installed  libdvdcss2.

---

### Post by FinalShot on 2010-05-23
I've played stargate before, both on linux & windows vlc.

And yes I have installed " libdvdcss2", that was in the link I provided...

And it appears it was just that individual dvd, others work.

---

### Post by mc4man on 2010-05-23
There may be something about the menu or dvd structure vlc doesn't like,  - you could always try ( blue is generally 0, may be 1 
```
vlc dvdsimple:///dev/sr[COLOR="Blue"]0[/COLOR]
```

or from media - > open disk -> no dvd menus

or to try opening a title directly
Ex. - title one
```
vlc dvd:///dev/sr0@1
```

---

