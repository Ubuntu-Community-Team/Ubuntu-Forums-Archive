---
title: "Ubuntu 5.10 - not installing via BENQ DVD drive"
date: 2006-05-14
forum: General Help
---

### Post by biriuk on 2006-05-14
Hello guys,

I downloaded via bittorrent (Azureus) the DISKNAME  Ubuntu 5.10 "Breezy Badger" - Release i386. (DVD)
I tried the liveCD option and it worked fine on an older AMD Duron 700Mhz, with DVD-Rom Liteon.
Now I want to install it on my desktop (AMD64, ATHLON 2800+, Benq DW1640).

The DVD is booting without problems, I can see the liveCD starting, I am choosing language, etc ... 
but it fails with this error: .... breezy ... /main/binary-i386/packadges failed the MD5 checksum ...
I checked the md5 checksum for ../packadges(.gz?) and it is OK. remember, it work fine on my other box.

I think there might be some incompatibility with the BENQ drive? I had problems installing KNOPPIX on this drive too, but I solved it turning off DMA with a boot parameter. 

Any ideas?

b++

---

### Post by biriuk on 2006-05-14
I found the solution in a kubuntu forum post:

[http://ubuntuforums.org/showthread.php?t=82017](http://ubuntuforums.org/showthread.php?t=82017)

---
there is a bug that discusses this: 
[https://bugzilla.ubuntu.com/show_bug.cgi?id=16901](https://bugzilla.ubuntu.com/show_bug.cgi?id=16901)

The trick is:
live cdrom-detect/cdrom_hdparm=-d1
---

---

