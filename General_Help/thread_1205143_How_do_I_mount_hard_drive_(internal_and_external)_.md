---
title: "How do I mount hard drive (internal and external) on multiple profiles?"
date: 2009-07-05
forum: General Help
---

### Post by Teabicky on 2009-07-05
I have just created an additional profile for my wife as we have started using dropbox.  The problem that I have come across is that my 2nd internal 1tb hard drive and my external 250gb seagate usb drive can only be mounted on one profile at a time (I have to comletely restart my computer to get around this).  There must be an easier way.  

Any links or advise welcomed with thanks.

---

### Post by Boondoklife on 2009-07-05
If you unmount the drives and then try to login with the other and mount it does it work?

---

### Post by Teabicky on 2009-07-07
This does work but it is a bit of a pain.  I have to unmount both volumes, change profile, mount both volumes and reconfigure my dropbox.  Still a bit of a pain.

---

### Post by Boondoklife on 2009-07-07
Well you could try adding lines to your fstab to mount the drives by uuid. This should let them be mounted at boot time. This may give you issues later if you try to unmount the drive though as you need admin privs to do so.

---

### Post by Teabicky on 2009-07-22
O.K. Just tried editing fstab... gonna reboot now. Fingers crossed.


Used this to help me....

> [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Teabicky on 2009-07-22
Ok, that didn't work.  I have added the following line to fstab

> /dev/sdb2	/media/disk	vfat defaults,user,dmask=027,fmask=137 0	0

which was the advice of the above link.  Not only does the drive not mount but it wont even let me view it at all.  It gets all "You do not have the permissions necessary to view the contents of 'disk'" on me.  I have a feeling that it could be something to do with dmask and fmask but I am not sure.

---

### Post by nikhilk on 2009-07-22
> **Teabicky said:**
> Ok, that didn't work.  I have added the following line to fstab



which was the advice of the above link.  Not only does the drive not mount but it wont even let me view it at all.  It gets all "You do not have the permissions necessary to view the contents of 'disk'" on me.  I have a feeling that it could be something to do with dmask and fmask but I am not sure.

See if changing user to users helps. According to the man page the difference between the two options is:
user   Allow an ordinary user to mount the file system.  The name of the mounting user is written to mtab so that he can unmount the file system again.
users  Allow every user to mount and unmount the file system.

The permissions issue might be unrelated.

---

### Post by Teabicky on 2009-07-22
That didn't work, I still had the same problem.  I tried changing the mount point too but now I can't find the drive anywhere.....  fstab.  My fstab line looks like this..
> 
/dev/sdb2	/mnt/internal	vfat defaults,user,dmask=027,fmask=137 0	0

---

