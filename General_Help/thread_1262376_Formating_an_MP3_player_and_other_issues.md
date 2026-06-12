---
title: "Formating an MP3 player and other issues"
date: 2009-09-09
forum: General Help
---

### Post by Cilionelle on 2009-09-09
Hi guys.  I've been using Ubuntu for several years now, and after initial problems with wifi and display size (seems reasonably common!), I'm happy to say that 9.04 is working really well, the best yet.

However, there are a few niggling little things that I'm having trouble with and would appreciate some help working out.

1. I have an MP3 player that is giving me jip.  It has a 256Mb memory, but consistently says that there is only 34Mb remaining on the drive.  In attempting to format it, via **gparted**, I get an error message:
```
Could not initialise connection to hald.
Normally this means the HAL daemon (hald) is not running or not ready.
```
How do I get hald ready and running?

2. I also have a separate partition of 53Gb that I cannot access, due to stuffing up the resizing of the partition a while back.  I previously received an error message for that too under 8.04, but since upgrading, the link on the taskbar does nothing, not even an error message.  I was told when I asked about it when it first occurred that I needed to use gparted to help out, but I don't have a clue as to how to go about that!

Cheers,
Cilionelle

PS: I realise I need to change my sig, but I'm too lazy. ;)

---

### Post by earthpigg on 2009-09-09
is there important data on that 53gb partition?

if not, try using gparted to delete that partition and create a new one. make sure you are using gparted when booting from a liveCD, of course.

---

