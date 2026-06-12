---
title: "Corrupt ext3 partition"
date: 2011-11-01
forum: General Help
---

### Post by jobelz on 2011-11-01
Good day people!

I've been trying to fix this disk for a week now, but everything I tried hasn't been working. I'm a linux starter however, so that doesn't help. 

The drive in question is a 120G Maxtor that was housed in a NAS. After a power outage the NAS reported the disk as empty. I took it out and assumed a hardware error. I have access to a harddisk hardware test suite but all those tests indicated that the disk is fine. The NAS runs an embedded linux (debian based I believe) and has ext3 partitions so I started looking around for possible solutions and installed it in my Ubuntu 32 bit machine.

Using ddrescue an image was made, it reported 10 errors (45056B). I took a 1TB drive and installed that as secondary disk with two partitions. One holding the image, one to hold the extracted image. When running e2fsck on that extracted image it reported a bad magic number in the superblock. I tried other superblocks and the last one worked (102400000), however, the system ran out of memory trying to fix errors (4Gb system memory). I decided to run Ubuntu 64 bit live cd and hope that would solve the memory issue, but the issue remained. I then booted my main machine (12Gb memory) with Ubuntu live 64bit, but alas, out of memory again.

At this point my hair is turning grey and I'm seeing linux commands in my sleep (good, I'm learning!). I decide to try some datacarving. Foremost and Photorec worked but the amount of usable files was pretty low and a lot didn't show up.

At an end, I ran Testdisk and Parted. Both detect partitions but seem to think they're ext2. After they do their thing I still can't access it though (possibly I'm doing something wrong, this was late last night).

Does anyone know how to fix the issue or what I could try next?
Thanks for any advice you can dispense. :)

J.

---

