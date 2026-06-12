---
title: "mount compressed disk image"
date: 2009-11-15
forum: General Help
---

### Post by bernardfrancois on 2009-11-15
I was wondering if it's possible to mount a compressed disk image (without first decompressing it offcourse).

Such an image could be created using dd in combination with gz, for example:
```
dd if=/dev/sda1 | gzip > /path/to/backup/sda1.image
```

I googled a bit, and the only thing I found were some people with the same question, but with no real answers:
[LIST]
[*][http://www.linuxquestions.org/questions/linux-desktop-74/mount-gzipped-hd-image-504510/](http://www.linuxquestions.org/questions/linux-desktop-74/mount-gzipped-hd-image-504510/)
[*][http://www.usenet-forums.com/linux-administration/126987-mount-gziped-compressed-image.html](http://www.usenet-forums.com/linux-administration/126987-mount-gziped-compressed-image.html)
[*][http://ask.slashdot.org/article.pl?sid=00/09/13/2246249&mode=thread](http://ask.slashdot.org/article.pl?sid=00/09/13/2246249&mode=thread)
[/LIST]

I did find something about a file system called AVFS, wich can mount compressed files (but not compressed disk images with arbitrary file systems in it):
[http://www.inf.bme.hu/~mszeredi/avfs/](http://www.inf.bme.hu/~mszeredi/avfs/)

Anyone has a clue if or how this could be done?

---

### Post by lloyd_b on 2009-11-15
Try Googling "cloop" - this is a Knoppix trick to setup a compressed file as a block device, which can then be mounted.

Note that this will be read-only access (creating a compressed, read-write, block device is an order of magnitude harder).

Now the bad news - this requires compiling a kernel module, so if you aren't comfortable doing this this may be a no go.

I have never used this, so you're on your own if you want to try it...

Lloyd B.

---

### Post by bernardfrancois on 2009-11-16
Read-only mounting is no problem. But I'm not just talking about mounting a compressed file; I mean mounting a file system inside a compressed file.

Do you think it would be possible to write something running in user space that passes uncompressed data to a kernel module that interprets the data as a certain file system?
If so, it may already exist...

---

