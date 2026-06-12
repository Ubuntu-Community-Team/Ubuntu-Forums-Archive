---
title: "Mount cellphone to ubuntu"
date: 2012-06-21
forum: General Help
---

### Post by poolhustler on 2012-06-21
Hi, I'm having trouble to mount my cellphone to Ubuntu. It shows as an icon where the other icons for the drive, usb etc are, but I get this message when I rightclick on it:

failed to mount samsung gt-s5570 card.

Maybe it is not even possible to mount it because the phone has another OS?

Anybody who knows how to do this?

Thanks

I have Wine installed but the phone does not show where the other programs like iTunes, Spotify etc shows.

---

### Post by Mark Phelps on 2012-06-21
You don't actually mount the "phone"; instead, what you do is mount the filesystem(s) the phone uses.  On my Android HTC phone, it mounts the internal memory filesystem as one partition and the SD card filesystem as another partition.

Also, when I connect my phone, I get a popup menu asking me what I want to do.  If I do not select "disk drive", it connect my phone for charging purposes only, meaning, it doesn't mount any filesystems.

---

