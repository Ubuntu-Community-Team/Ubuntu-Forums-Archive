---
title: "external usb hard drive really slow after some time"
date: 2006-02-11
forum: General Help
---

### Post by dragonflyFZX on 2006-02-11
hi,

i have an external usb harddrive of about 200Gig (maxtor) that is fat32.  If i want to copy a file to this drive, it is very slow (about 1.5 Mb/s).  However, sometimes i get much better speeds, in the order of 11Mb/s.  This is especially so when i just start copying.  But after a while, the speed goes down significantly.  i am running kubuntu breezy...

---

### Post by dcstar on 2006-02-11
[QUOTE=dragonflyFZX]hi,

i have an external usb harddrive of about 200Gig (maxtor) that is fat32.  If i want to copy a file to this drive, it is very slow (about 1.5 Mb/s).  However, sometimes i get much better speeds, in the order of 11Mb/s.  This is especially so when i just start copying.  But after a while, the speed goes down significantly.  i am running kubuntu breezy...[/QUOTE]
Do you have DMA enabled? (do a search if not).

---

### Post by dragonflyFZX on 2006-02-12
[QUOTE=dcstar]Do you have DMA enabled? (do a search if not).[/QUOTE]

```
bjvca@dragonfly:~$ sudo hdparm /dev/sda1

/dev/sda1:
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 24792/255/63, sectors = 398283417, start = 63
bjvca@dragonfly:~$ sudo hdparm -d1 /dev/sda1

/dev/sda1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
bjvca@dragonfly:~$ hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:    4 MB in  5.40 seconds = 758.63 kB/sec
BLKFLSBUF failed: Permission denied
bjvca@dragonfly:~$       
```

i guess it is a sata drive, though i dont know what that means technically...  The strange thing is that it often starts at a very good rate, but then falls back.

---

