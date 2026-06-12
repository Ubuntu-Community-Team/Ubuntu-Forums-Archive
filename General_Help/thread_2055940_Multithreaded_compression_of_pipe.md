---
title: "Multithreaded compression of pipe?"
date: 2012-09-10
forum: General Help
---

### Post by lupoph on 2012-09-10
Hello!

I am currently using an Ubuntu 12.04 live CD for partition management tasks. In particular I use "ntfsclone" for creating a n efficient backup of my C:\ drive.

At 75 GB I'd really like to compress the image. However, using 
```
ntfsclone -s -o - /dev/sda5 | gzip --fast - > IMGFILE
```
is pretty slow -- at least by a factor of two slower than writing the uncompressed data to the USB3-HDD. Even without compression the transfer takes about an hour though.

Running on a Quadcore processor, I wondered if there is any compression tool that supports multithreaded compression of a pipe. 

Being used on a Live-CD (a Live-USB-stick sadly fails to boot) I'd prefer the software (if any) to be easily installable, without fiddling with package sources, i.e. multiverse repositories are disadvantageous. 

Does any software fulfill these criterions?

---

