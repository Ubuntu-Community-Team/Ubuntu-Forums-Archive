---
title: "Finding out DVD/CDRW speed in Linux"
date: 2010-07-05
forum: General Help
---

### Post by NFblaze on 2010-07-05
How would I go about finding out the "x-by-x-by-x" write speeds of my burner.

I happened to cat /proc/sys/dev/cdrom/info
It output something inspecific like

drive name:		sr0
drive speed:		24


Is there a way to gather more information?

---

### Post by mandar.mitra on 2010-07-05
You could try the following:


1. /usr/bin/dvd+rw-mediainfo. This'll give you information about the media that's actually loaded, but that should give you some idea about what your drive supports.


2. dmesg. On my machine, this says, for example:


sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray



Sorry for not giving a more precise answer.

---

### Post by NFblaze on 2010-07-05
mandar.mitra,

Thanks for your reply. I was doing some research myself, I must say that there doesnt seem to be a method. Though, thanks for your lovely reply.

---

