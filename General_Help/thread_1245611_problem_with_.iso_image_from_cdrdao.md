---
title: "problem with .iso image from cdrdao"
date: 2009-08-20
forum: General Help
---

### Post by lyratzis on 2009-08-20
Hey,

I made an iso image of a cd using cdrdao but I cannot get it to mount to my virtual drive; when I type

**sudo mount -o loop -t iso9660 ~/wwp.iso /media/cdromv**

it gives me mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error

so apparently it isn't an iso 9660 image? The command I used to rip it was

**cdrdao read-cd --read-raw --datafile wwp.iso --device /dev/cdrom --driver generic-mmc-raw wwp.toc**

how I can I get this to mount?

---

### Post by jocampo on 2009-08-20
Check the iso file ;-)

```
md5sum MyFile.iso
```

Just to be sure your ISO has no problems .... that would be my 1st step ... checksum must be equal to source file ...

---

### Post by lyratzis on 2009-08-20
sorry, how do I find a hash value from the cd to which I can compare the md5sum from the iso I ripped?

---

### Post by lyratzis on 2009-08-24
any other ideas as to what could be wrong / what I should be trying to fix it? if this information is useful, the ripping process took quite a long time, and cdrdao gave me a ton of L-EC errors. I thought this was just part of the copy protection and they were ignored, but maybe I am mistaken. at any rate, I still can't get the iso to mount

---

