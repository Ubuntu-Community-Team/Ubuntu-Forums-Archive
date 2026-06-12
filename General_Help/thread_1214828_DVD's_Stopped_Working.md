---
title: "DVD's Stopped Working"
date: 2009-07-16
forum: General Help
---

### Post by guppygould on 2009-07-16
Hey all!

Just as I've finished installing and setting up my new install with all the programs I like, the DVD playback has stopped working in Totem and VLC.

When I try to open a DVD in Totem it crashes and VLC just gives me "VlC cannot read the file." I'm pretty sure I have all the correct packages installed because it was working a week ago. 

Does anyone have any solutions to this? I really don't want to do a clean install again if it can be helped.

Thanks in advance,

-Leo

---

### Post by guppygould on 2009-07-16
Bump?

---

### Post by Firestem4 on 2009-07-16
Can you run Totem and VLC from the terminal and copy the output when you insert and try to play a DVD?

---

### Post by guppygould on 2009-07-16
> libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: CHUCK_SEASON_1_DISC_4
libdvdnav: DVD Serial Number: 38C588DA
libdvdnav: DVD Title (Alternative): CHUCK_SEASON_1_DISC_4
libdvdnav: Unable to find map file '/home/guppygould/.dvdnav/CHUCK_SEASON_1_DISC_4.map'
libdvdread,ifoOpenVMGI(): Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"

Any ideas?

---

### Post by Firestem4 on 2009-07-16
It looks as if it can't detect there is libdvdcss installed on your computer. Try redonwloading/installing the libdvdcss. (AFAIK they should be in the medibuntu repositories. I usually get them from a shell script included in kaffeine media player). (Directions for that can be found in the kubuntuforums.org)

Just out of curiousity. Is this from Totem or VLC?

---

### Post by guppygould on 2009-07-16
That was VLC, Totem kicks out a similar error though. I'll give that a go. I just tried reinstalling libdvdread and that didn't work.

---

### Post by guppygould on 2009-07-16
> libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: CHUCK_SEASON_1_DISC_4
libdvdnav: DVD Serial Number: 38C588DA
libdvdnav: DVD Title (Alternative): CHUCK_SEASON_1_DISC_4
libdvdnav: Unable to find map file '/home/guppygould/.dvdnav/CHUCK_SEASON_1_DISC_4.map'
libdvdread,ifoOpenVMGI(): Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
[00000412] main access error: no access module matched "dvd"
[00000408] main input error: open of `dvd:///dev/sr0' failed: could not create access: no access module matched "dvd"

That's the VLC error I get now after installing libdvdcss.

---

### Post by guppygould on 2009-07-16
Bump.

---

### Post by guppygould on 2009-07-16
There's no need to help me now because I've sorted it, but I wouldn't have without the suggestions in this thread. So thanks for the advice.

If anyone is interested in the problem it was to do with when I gave my account a username and password. My account priveleges were changed without me knowing (including DVD playback.)

---

### Post by mc4man on 2009-07-16
sorted out

---

