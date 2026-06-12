---
title: "K3B - Wont burn discs"
date: 2009-12-27
forum: General Help
---

### Post by Zack_PSP on 2009-12-27
I have used K3B in the past and it always worked without a hitch...

I get the error : cdrecord has no permisson to open the device.
I have tried loads of different permissions, creating a burning group etc to no avail.

( Also wasted 10 discs so far :( )

K3B Version : 1.68.0
Ubuntu Version : 9.10

I've googled the hell out of this but no joy as yet.

Thanks in advance.

---

### Post by RedSingularity on 2009-12-27
Have you tried opening the program as root?

---

### Post by Zack_PSP on 2009-12-27
Yeah, same error. :(

---

### Post by Zack_PSP on 2009-12-27
Ok so after some more messing I managed to get rid of that error.

However of course, there are new ones.

I now get (at the end of cd burning) : 

Probably a buffer underrun occurred
Please choose a lower speed 

I tried another two discs with a lower speed and the same error occurred. Buffer underrun protection is enabled.

hmmm ?

---

### Post by efflandt on 2009-12-27
Are you burning CD-R or CD-RW?  I have never had any problems with CD-R using Brasero or anything else full speed, but not much luck with Brasero or k2b for CD-RW (maybe my room is too cool or drive too old).

Try unmounting the disk if it auto mounts and see if you then have permission.

I got one good CD-RW disk with k3b, but then the next time it hung burning indefinitely (probably ruined the disk after burning for a couple of hours).  I could not cancel or kill it and had to shutdown to stop it.

---

### Post by Zack_PSP on 2009-12-27
> **efflandt said:**
> Are you burning CD-R or CD-RW?  I have never had any problems with CD-R using Brasero or anything else full speed, but not much luck with Brasero or k2b for CD-RW (maybe my room is too cool or drive too old).

Try unmounting the disk if it auto mounts and see if you then have permission.

I got one good CD-RW disk with k3b, but then the next time it hung burning indefinitely (probably ruined the disk after burning for a couple of hours).  I could not cancel or kill it and had to shutdown to stop it.

CD-R. And the permission errors are gone now. Just the buffer underrun errors remain. Brasero also errors out at the end, it doesn't explain why though (according to the log)

Edit : just tried nero and it gave me : "illegal disc"

Maybe my internal dvdrw/cdrw drive isnt using the right driver or something. I will try an external drive to rule it out

Edit 2 : Ok the external dvd/cd writer worked perfect in k3b. It showed up correctly as DVD/CD burner. My internal drive only shows up as DVDRAM... I'm at a loss as to how to fix this now, besides the obvious switch over of drives.

---

### Post by jl2035 on 2009-12-27
I had this problem with Brasero, and I solved it using K3b. But this wasn't my only bad experiance with cd burning. I already had this kind of problems on a few other computers. 

I'll never understand why is CD burning such a big deal for linux, when it can do almost everything else like other operating systems.

---

### Post by sparks40 on 2009-12-30
I'm having a similar problem burning DVD's, although burning CD's seems to be working fine.

When I try to burn a DVD I get the error message that "cd record has no permission to open the device". A second message tells me that I can "use k3bsetup to solve the problem"... but does not explain exactly what it wants me to do. Using k3b as root does not make any difference.

As other responses to this post are kind of old I can only hope that someone has found a solution to the problem. k3b is an excellent piece of work and I have burned 100's of CD's without creating any coasters. I trust that the same can be said about DVD's as well.

k3b version 1.68.0
Ubuntu 9.10 (with all the latest updates)


Thanks.

---

