---
title: "External Drive:  why use NTFS  ?"
date: 2012-09-04
forum: General Help
---

### Post by George Heine on 2012-09-04
Recently purchased a [SIZE=2]Toshiba Canvio External Portable Hard Drive.  Primary purpose is backup storage.  Relabeled the device with

[/SIZE]```
sudo ntfslabel  -v /dev/sdb1 toshiba

```[SIZE=2]
and put the following line in /etc/fstab:

[/SIZE]```

LABEL=toshiba /media/toshiba ntfs rw,use,noauto 0 0

```This produces the error 

[QUOTE]
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. 

Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. 

Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
[/QUOT

Yuck!   Is there any reason why I shouldn't just reformat the drive?  I do want to use something Windows-readable (in an emergency, maybe I'd have to borrow a Windows PC to get at the data), but why not just plain old VFAT?

My sketchy knowledge of the differences between VFAT and NTFS:  NTFS is more secure (not relevant here, this is a home PC) and slightly more efficient in storage space.  Also NTFS may allow larger file sizes (how big?) and seems to support symbolic links.   These are minor but not insurmountable obstacles.

So, my question, for an external drive used for backup storage, is there any good reason to use NTFS rather than VFAT or something else?

---

### Post by cortman on 2012-09-04
> **George Heine said:**
> Recently purchased a [SIZE=2]Toshiba Canvio External Portable Hard Drive.  Primary purpose is backup storage.  Relabeled the device with

[/SIZE]```
sudo ntfslabel  -v /dev/sdb1 toshiba

```[SIZE=2]
and put the following line in /etc/fstab:

[/SIZE]```

LABEL=toshiba /media/toshiba ntfs rw,use,noauto 0 0

```This produces the error 

Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. 

Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. 

Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)


Yuck!   Is there any reason why I shouldn't just reformat the drive?  I do want to use something Windows-readable (in an emergency, maybe I'd have to borrow a Windows PC to get at the data), but why not just plain old VFAT?

My sketchy knowledge of the differences between VFAT and NTFS:  NTFS is more secure (not relevant here, this is a home PC) and slightly more efficient in storage space.  Also NTFS may allow larger file sizes (how big?) and seems to support symbolic links.   These are minor but not insurmountable obstacles.

So, my question, for an external drive used for backup storage, is there any good reason to use NTFS rather than VFAT or something else?

Why relabel it?
You can specify the mount point in fstab without relabeling.
On a related note, it's best to mount drives using the UUID rather than the label. You can find the UUID by running

```
sudo blkid
```

Your main problem though seems to be a typo-

```
LABEL=toshiba /media/toshiba ntfs rw,**use**,noauto 0 0
```

**use** should be **user**.

---

### Post by doktorOblivion on 2012-09-04
I would suggest keep it simple.  When I go native and mount one of my win7 or winXP dual boot drives, I use something like:

/dev/sde5 on /media/<my win storage> type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

When I go remote, I use something like:

sudo mount -t cifs //<my win machine>/z\$/tmp /home/<myhomedir>/<mymountpoint>/ --verbose -o user=Administrator,pass=<my pass>,rw,uid=<my uid>


Hope this helps...

---

### Post by Morbius1 on 2012-09-04
I'm confused. This is an external USB drive? Why are you trying to mount it through fstab?

Now that you've changed it's label it will autocratically mount to /media/toshiba whenever it's turned on or inserted.

---

### Post by spjackson on 2012-09-04
For the backup operation you describe, the main reason to choose NTFS over VFAT is maximum file size: 16 million TB vs 4GB. I think that VFAT may also be more restrictive in the character set permitted in filenames, and also path length. However, I don't recall the details on these latter points, and I may be imagining it.

---

### Post by George Heine on 2012-09-06
Thanks, SPJackson, you answered the question of the important difference, for backup applications, between VFAT and NTFS.  I'll mark this thread as "Solved".  

Will keep doktorOblivion's response handy for next time I need to add a Windows filesystem mount to /etc/fstab.

Thanks also to the other respondents for taking a look.
To briefly answer some of the other questions raised:

Relabeled the drive because the manufacturer's default ("TOSHIBA\ EXT") contained  embedded spaces.  Just a habit to avoid potential problems.

Had in fact tried changing the fstab reference from LABEL= to UUID -- same error.  

Typo ("use" not "user") was  in my post, but not in the fstab.  Guess I should have previewed (probably would have caught the bad close-quote also.)

GH

---

