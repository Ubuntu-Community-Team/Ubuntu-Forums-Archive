---
title: "Garbaged DVD Playback"
date: 2011-11-09
forum: General Help
---

### Post by trogbot on 2011-11-09
Had a computer melt down & had to reload only OS I had on hand which was Ubuntu 10 LTS.  Everything back to norm except for DVD playback.  No matter which app I use with it (VLC/MPlayer/etc.); everything is choppy and garbled.  Anyone had this happen recently & what might I try to fix.  All/Any help appreciated.  Thanks in advance.

---

### Post by andrew.46 on 2011-11-09
The answer may be here:

Restricted Formats Playing DVDs
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by trogbot on 2011-11-09
I had found that & gave it a try. It returned:

The following packages were automatically installed & no longer necessary.
 linux-headers-2.6.32-33 linux-headers-2.6.32-33-generic

It says I can use "Use 'apt-get autoremove' to remove them.".  Will this do any good since they're already there?

Any help appreciated.:(

---

### Post by andrew.46 on 2011-11-09
You can ignore that message quite safely if you are simply after dvd playback, although as a 'housekeeping' measure you can do as your system suggests and remove the extraneous headers at some stage.

---

### Post by trogbot on 2011-11-09
Thanks for the info.  Removed them & did'nt make any diff.  I remember back to when I was running ubuntu 9.? that I had to load a proprietary driver for my ATI Radeon 9600.  Does this info give any clues to what it might be?
Thanks in advance.:confused:

---

### Post by trogbot on 2011-11-10
Bump Update.  Played around some more on this problem & found that old DVD's play fine (apparently no DRM).  The lib "libdvdread4" is installed, which if I understand correctly, contains the old "libdvdcss2" which allowed playing encrypted disks.  Is this correct?; and if so, any advice on where to look next.  Thanks.

---

### Post by SeijiSensei on 2011-11-10
Some newer DVDs use the ARccOS method for content protection.  A quick Google search suggests that Linux has problems with these types of DVDs because they're not encrypted with CSS.  The current Ubuntu [documentation]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs") for DVD ripping ends with this paragraph:

> Note that with some recent DVD films, *all* current Linux DVD rippers have problems reading the disc due to newer copy protection schemes such as ARccOS or RipGuard. The same is true even of the latest version of DVDshrink on Windows, and only certain tools like DVD2HDD, DVD Decrypter, and AnyDVD (Windows programs) can handle the newer copy protection mechanisms. 

---

### Post by trogbot on 2011-11-10
Thanks for the info SeijiSensei.  Is there any indication on the disc which reflects this new protection scheme?

---

