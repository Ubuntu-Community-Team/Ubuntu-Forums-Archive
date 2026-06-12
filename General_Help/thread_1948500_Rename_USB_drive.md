---
title: "Rename USB drive?"
date: 2012-03-28
forum: General Help
---

### Post by Chip88 on 2012-03-28
Hi there!

I tried everything what was suggested here in the board and what I found by searching in Google, but I couldn't get it work!!!

I have Oneiric 11.10 and my aim was to rename a USB drive (FAT32).

I did the following:
```
sudo mlabel -i /dev/sdc ::"Chipy"
```

The command 
```
sudo blkid
```

says I labeled everything right: 
```
/dev/sdc: LABEL="CHIPY" UUID="C461-F40B" TYPE="vfat" 
```

But anyway Dolphin shows the description of the USB drive and NOT the label; see attached file!

Why does this happen? What do I have to change to let the label also appear in Dolphin?

Thanks in advance for your help!

Regards,
Chipy

---

### Post by winh8r on 2012-03-28
I don't use kubuntu, but you can use the Disk Utility, if you have not got it installed , you can get it from the repositories and you can rename your disks and flash drives using that.

```
sudo apt-get install palimpsest
```

Hope this helps.

---

### Post by Chip88 on 2012-03-28
@ winh8r:
Thanks for your very fast answer!

I had already palimpsest installed.

And you're right: I can rename everything and it appears also suddenly and correct in Dolphin, BUT: This usb drive I am fighting with doesn't change his name in Dolphin!!!

It stays everything as it is in the attached pic. DAMN!!!

---

### Post by Chip88 on 2012-03-29
Hey guys!

**Good news!!! Problem solved finally!!! ;)**

"Playing" with palimpsest and comparing my usb drives, I realised the one usb drive, which name I couldn't change, was not partitioned!

Changing this by choosing FAT and so on (there are enough instructions here in the forum and in the web, how to do it!), made it possible to change the name finally!!!

The problem is finally gone!!! CARAMBA!!! :guitar: :lolflag:

Thank you very much for all your help, guys!!!

Chipy

---

### Post by winh8r on 2012-03-29
Sorry I couldn't get back sooner, but I did wonder about that being the case.

Glad you got it worked out!

Good Luck.

---

