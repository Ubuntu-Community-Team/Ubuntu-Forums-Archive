---
title: "Testing the integrity of an ISO image"
date: 2006-02-06
forum: General Help
---

### Post by ksenos on 2006-02-06
Hello to everyone.

I am backing up my old CD (up to 10 years old) by creating ISO images and burn  ing them in DVDs. I am using the following command to create the ISO images.
```
dd conv=noerror if=/dev/hdd of=<VOLUME NAME>.iso
```
On the above, the /dev/hdd coresponds to my CDROM drive. 

First, I would like to ask if the above is a wise to create ISO images. 

Second, is there a utility that would check if an ISO image is created correctly (by cross-checking the TOC and included files, or something)?

Thanks a lot.

Kostas.

---

### Post by krusbjorn on 2006-02-06
I had the same question and ran across cpverify a few weeks ago. See if it suits your needs!

[http://www.unixreview.com/documents/s=9846/ur0508a/ur0508a.html](http://www.unixreview.com/documents/s=9846/ur0508a/ur0508a.html)

---

### Post by ksenos on 2006-02-06
Thanks a lot :D :D :D. This utility is very close to what I am looking for, but it is a little hard to use in my case. I must first mount the ISO image as root, insert and mount the CD-ROM from which the image is created and run the cpverify script. What I say might silly, but I got a few hundreds of CDs and this will take... well, too long ;).

EDIT: Just forget what I say above, cpverify fits my needs. Any other ideas are still welcome though. Thanks a lot :D.

---

