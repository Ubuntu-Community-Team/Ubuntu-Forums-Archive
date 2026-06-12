---
title: "md5sum: /dev/cdrom: Input/output error"
date: 2010-04-29
forum: General Help
---

### Post by robert shearer on 2010-04-29
Having downloaded Lucid Desktop i386 and verified the md5 for the download I then burnt a cd.

When I try to verify the cd with 
```
md5sum /dev/cdrom
```
It returns  ```
 md5sum: /dev/cdrom: Input/output error
```

Download was from local mirror (NZ) and the same fault happened when I downloaded and burnt the Alternate image.

Until now this has worked perfectly on this machine with other  md5sums for  cd's  matching their downloaded md5sums.

Anyone else having this error ?

Thanks in anticipation.

**Edit** 
 Booted into a Jaunty install on the same machine and tried **md5sum /dev/cdrom** from there with the same error returned.

Thinking it may be a Lucid bug I reburned the cd using Brasero in Jaunty but **still** the problem persists.

Surely it can't be the (nearly new) burner ? 

Then the aha moment when I saw I had K3b installed here and remembered that none of the Gnome burning software has ever worked correctly for me !!.

Reburned with K3b and all is sweet. Md5sum from the cd is read and correct.

Any guesses as to why appreciated. My guess is that it has to do with only having ide/pata drives and Gnome being optimised for sata nowdays??.

Oh well, once again I  have to install K3b and all that it brings with it just to get reliable and verifiable burning.
Had hoped that Lucid would fix this.

---

