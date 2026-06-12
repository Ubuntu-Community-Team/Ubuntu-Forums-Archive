---
title: "a problem when playing music"
date: 2009-07-06
forum: General Help
---

### Post by pc@rs2006 on 2009-07-06
when i use rhythmbox to  play music ,there are so many errors.i have mounted the file system (fat or fat32 or ntfs)where music file is.if using movie player (play music),there is  a report
an error occurred:
the audio device is busy .is another application using it?
how i should do? it also happens when i play music in my mp3 player

---

### Post by pmlxuser on 2009-07-06
would try scanning the device fro errors. and correcting the errors if any.

by the way have you tried restarting your machine and the remounting the file system??

---

### Post by johnadverd on 2009-07-06
[I]Hi,
Rhythmbox[/I] cannot *play music* files. This question was originally filed as bug #196101. Binary package hint: *rhythmbox*. I'm trying to *play music* files.*Rhythm box* downloaded from a cd fine but it wont *play* the *music* although it says its playing but no sound. when I tried to *play* direct. I solved this *problem* in Hardy 8.04 alpha 3 i386 by specifying the ALSA driver. The could be a *problem* with hardware auto detection on your computer.

---

### Post by Etelerix on 2009-07-06
try moving the music file to your music folder directory. Also check for updates and install any codecs there are for mp3 and video.

---

### Post by pc@rs2006 on 2009-07-07
> **pmlxuser said:**
> would try scanning the device fro errors. and correcting the errors if any.

by the way have you tried restarting your machine and the remounting the file system??
i have tried as you say,but it did no work.also did by songbird,well,it reports:Failed to connect stream:Invalid argument

---

### Post by Megrimn on 2009-07-07
sounds like a sound driver conflict.

Make sure every driver is set to ALSA, in System > Preferences > Sounds *and* in the programs you are using.

It used to happen when in Amarok when I would plug in any usb device.  I changed the driver in Amarok from 'default' to 'ALSA', and that fixed it.

---

