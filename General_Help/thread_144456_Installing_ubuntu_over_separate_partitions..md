---
title: "Installing ubuntu over separate partitions."
date: 2006-03-14
forum: General Help
---

### Post by radiohead on 2006-03-14
Hello. I have a 250 gig HDD and a separate 4.3 gig HDD. The 250 gig is separated into 3 partitions. 5 gigs for ubuntu, 5 gigs for windows, and 240 for a cross-over partition. On the 240 gig partition, it is fat32, so it is both readable by Windows and Linux. I would like to setup this partition so that when I install anything, it installs to that partition, not the 5 gig one. So, when I run 

```

sudo apt-get install foo

```

it installs foo to the fat32 partition.

Do I need to make this partition my /root directory? and if I do that, how would windows react to it being like that?

---

### Post by evilgold on 2006-03-14
Linux doesnt organize its program files the same way as windows does (in one folder called "program files"). Its really not a good idea to try and have things installed to a shared partition, it would look rather odd. I also dont know if its possible, because you'd have to  have your / or at least /usr as a fat32. 

you could however mount the /home folder on your fat32 partition and keep your personal folders shared.

---

### Post by yanik on 2006-03-14
One better way would be to format your 250GB as ext2 and install a driver for windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Then mount that drive on /usr

---

