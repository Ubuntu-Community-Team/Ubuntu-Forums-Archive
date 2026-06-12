---
title: "Nautilus and Data DVDs"
date: 2006-03-10
forum: General Help
---

### Post by bluevoodoo1 on 2006-03-10
I'm trying to burn data on some DVD+R discs. I've seemingly had successful burns with k3b and Nautilus (no errors from either), yet when I try to read them through Nautilus it just claims that it's blank. The drive is an [Asus]("http://www.newegg.com/product/product.asp?item=N82E16827135046") DVD +/- R. The media are TDK. 

Here are a few lines from dmesg
```

[4299942.655000] hdb: media error (blank): error=0x80 { LastFailedSense=0x08 }
[4299942.655000] ide: failed opcode was: unknown
[4299942.655000] end_request: I/O error, dev hdb, sector 0
[4299942.655000] Buffer I/O error on device hdb, logical block 0
[4300263.632000] cdrom: This disc doesn't have any tracks I recognize!

```

There have been a few threads about this and nothing seems to have been resolved, nothing on google either. I hope this stack of 100 DVD+R discs aren't simply trash...

---

### Post by bluevoodoo1 on 2006-03-10
Hmm... well. I think this is an issue with the actual burning, not with Nautilus. I tried the disc in another computer and it didn't work... And I haven't really found any sort of guide or how-to stating compatibilies or solutions for burning DVD+Rs or DVD-Rs. Simply put, is burning a DVD data disc supported with *any* program?

---

### Post by akiro.yamamoto on 2006-03-11
I created a data dvd with Nautilus "//burn" with excellent results.
My media: Phillips 1-8x 4.7GB DVD+R (Valua media)
My Burner: NEC 3540A 16x DVD +/- R/RW DL drive
My drive is configured as IDE2 Master.

---

### Post by dcstar on 2006-03-11
[QUOTE=bluevoodoo1]I'm trying to burn data on some DVD+R discs. I've seemingly had successful burns with k3b and Nautilus (no errors from either), yet when I try to read them through Nautilus it just claims that it's blank. The drive is an [Asus]("http://www.newegg.com/product/product.asp?item=N82E16827135046") DVD +/- R. The media are TDK. 
.......[/QUOTE]
I assume you have the dvd+rw-tools package installed?

---

### Post by bluevoodoo1 on 2006-03-11
[QUOTE=dcstar]I assume you have the dvd+rw-tools package installed?[/QUOTE]

Yes, it's installed.

---

### Post by bluevoodoo1 on 2006-03-11
Just tried burning from the command line. Seems like it went well, there are a few strange comments, but the same still happens, still read as a blank DVD. The files were a bunch of audacity projects and wav files (about 1.7 gigs)... here's the output...

(I tried this twice, one without sudo, this one with)

```

bluevoodoo1@ubuntu:~$ sudo growisofs -Z /dev/hdb -R -J music/audacity
Executing 'mkisofs -R -J music/audacity | builtin_dd of=/dev/hdb obs=32k seek=0'
/dev/hdb: "Current Write Speed" is 8.2x1385KBps.
:-? the LUN appears to be stuck writing LBA=310h, retry in 70ms
:-? the LUN appears to be stuck writing LBA=310h, retry in 70ms
  0.55% done, estimate finish Sat Mar 11 12:45:41 2006
  1.09% done, estimate finish Sat Mar 11 12:12:17 2006
  1.64% done, estimate finish Sat Mar 11 12:02:09 2006
  2.19% done, estimate finish Sat Mar 11 11:55:32 2006
  2.73% done, estimate finish Sat Mar 11 11:51:35 2006
..................
 21.32% done, estimate finish Sat Mar 11 11:38:46 2006
:-? the LUN appears to be stuck writing LBA=30310h, retry in 70ms
 21.86% done, estimate finish Sat Mar 11 11:39:32 2006
.................
 97.83% done, estimate finish Sat Mar 11 11:36:46 2006
 98.38% done, estimate finish Sat Mar 11 11:36:45 2006
 98.92% done, estimate finish Sat Mar 11 11:36:45 2006
 99.47% done, estimate finish Sat Mar 11 11:36:45 2006
Total translation table size: 0
Total rockridge attributes bytes: 92750
Total directory bytes: 151552
Path table size(bytes): 148
Max brk space used c6000
914847 extents written (1786 MB)
builtin_dd: 914848*2KB out @ average 5.5x1385KBps
/dev/hdb: flushing cache
/dev/hdb: closing track
/dev/hdb: closing session
:-[ CLOSE SESSION failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
/dev/hdb: reloading tray
bluevoodoo1@ubuntu:~$

```

---

### Post by bluevoodoo1 on 2006-03-15
Ah HA!

Got it working. It didn't like my TDK DVD+R discs so I got some Verbatim DVD-R discs and it's working. Now I have ~90 DVD+R discs with no use....

---

### Post by Haegin on 2006-03-18
1. Flog em to somebody running windows
2. Wait untill you can use them on linux
3. Use them as coasters
4. Build a pc case out of them (somehow)
5. Hang em from bits of string over a vegetable patch to scare away birds
6. Sharpen the edges and throw to stop the birds ever coming back
7. Create modern art
8. Leave them in a corner gathering dust until they are antique and worth a fortune

---

