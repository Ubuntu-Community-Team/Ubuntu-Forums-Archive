---
title: "Strange Totem behaviour"
date: 2006-06-04
forum: General Help
---

### Post by ago on 2006-06-04
When I try to play a DVD with totem I randomly have one of the following 2 errors:

1) Failed to find mountpoint for /dev/hdc
2) The source seems encrypted, and can't be read are you trying to play an encrypted DVD wothout libdvdcss?

The wierd thing is that it works perfectly if I use: movie > open location > dvd://. CDs also work.

In fact the the mountpoint for /dev/hdc is in fstab and certainly works (I can mount monually without problems) and I have libdvdcss installed and working. I tried both totem-xine and totem-gstreamer. Same thing. I use xubuntu.

---

### Post by IceAxe18 on 2006-06-04
This is what my Movie menu looks like when I have a DVD movie in my dvd player. Does yours look like that? If so you should be able to click on Play Disc & it should play your movie or you can click on cdrom0 & the same thing should happen.

---

### Post by ago on 2006-06-05
If I click on "Play Disc" I have one of the errors above when a DVD is inserted.
Open Location = "dvd://" works. GXine works. CD works. "Open Disc" with DVD does not work.

---

### Post by ago on 2006-06-05
I guess it is similar to what reported here:

[http://bugzilla.gnome.org/show_bug.cgi?id=318401](http://bugzilla.gnome.org/show_bug.cgi?id=318401)

[https://launchpad.net/distros/ubuntu/+source/gnome-volume-manager/+bug/23256](https://launchpad.net/distros/ubuntu/+source/gnome-volume-manager/+bug/23256)

Anybody knows how to get around it (other than using gxine)?

---

