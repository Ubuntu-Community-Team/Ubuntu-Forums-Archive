---
title: "cannot play .dat files from cd"
date: 2010-01-04
forum: General Help
---

### Post by ydristi on 2010-01-04
hai i am using ubuntu 9.10 .i hve a philips  combo drive .
my problem is that i can't play .dat files from cd's ,there is no problem with dvd's & other files from cd's .when i checked the permissions it showed the owner as root also there is a lock symbol in .dat files that are already in my pc .this is my 1st post .....plse hlp me

---

### Post by howefield on 2010-01-04
Do you have the gstreamer plugins installed ?

Use Synaptic Package Manager and install

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg

---

### Post by ydristi on 2010-01-04
ya i hve .i can play the .dat  file that is already in my system but when i tried to play it or copy it from cd it don't work and the media player freezes. ?????

---

### Post by 3rdalbum on 2010-01-04
Are you talking about video CDs? (VCD)

You don't play or copy the files themselves from a VCD, just like you don't play or copy files from DVDs.

When you insert the VCD, go into Movie Player and go to File > Play Disc.

This is because VCDs are not just 'data discs' with video on them, they are differently formatted and cannot be read like ordinary data discs.

---

### Post by ydristi on 2010-01-04
thanks & it works but hw cn i copy it ??

---

### Post by amsterdamharu on 2010-01-04
vlc player can re encode dvd's and maybe avidemux.

With vlc choose dvd no menus and choose a sub and sound stream to encode.

---

