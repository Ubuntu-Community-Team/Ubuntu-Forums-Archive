---
title: "Tell Synaptic to look in /media/cdrom1"
date: 2006-04-18
forum: General Help
---

### Post by outofsync on 2006-04-18
Hi,

I installed Breezy in a desktop PC that has a CDROM in /media/cdrom (which points to /media/cdrom0) and a DVDROM in /media/cdrom1

I downloaded DVD ISO images of Breezy packages

Synaptic isn't able to detect /media/cdrom1 as a valid source, so when I use "Edit>AddCDRom" it complains it can't mount the cdrom (I added /hdd and /media/cdrom1 to /etc/fstab to make sure that it's in fstab).

So I used apt-cdrom, and with the "-d=/media/cdrom1", it was able to add the new DVD ISO repositories successfully.

However, if I start Synaptic and I try to install a package from those repositories, it insists to search in /cdrom/ (so it can't find anything there, and I can't even put a DVD in that unit because it's a CD unit, not a DVD unit).

Is there any way for telling Synaptic something like "please, would you be so kind of forgetting that /cdrom/ and /media/cdrom0/ exist" ?

Thanks

---

### Post by Qrk on 2006-04-18
Try editing your /etc/apt/sources.list

```
sudo gedit /etc/apt/sources.list
```

The first line should look something like this:

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

Try changing it to point to cdrom1

> deb cdrom1:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

I haven't tried the DVD, but it shouldn't make a difference. I wouldn't change anything besides adding the 1 ... unless you are missing that line entirely.

---

### Post by outofsync on 2006-04-21
Thanks a lot!

---

