---
title: "LVM, want to get rid of volume group but can't"
date: 2010-03-08
forum: General Help
---

### Post by herbster on 2010-03-08
I bought a new drive and moved all data from my volume group to it, now I just want to get rid of the vg completely, but can't:

```
&#9492;&#9472;> sudo lvchange -a n /dev/mapper/dabox-stuff 
Password: 
  LV dabox/stuff in use: not deactivating
```

and

```
&#9492;&#9472;> sudo vgremove dabox
Do you really want to remove volume group "dabox" containing 1 logical volumes? [y/n]: y
  Can't remove open logical volume "stuff"
```

I just want to wipe it and format the disks.

TIA for any help :)

---

### Post by bodhi.zazen on 2010-03-08
If there is nothing on it, simply reformat it.

From the error message I am guessing you need to unmount and deactivate the partitions / logical volumes. Along those lines, what is "stuff" ? do you have more then one logical volume ?.

the error messages are telling you your volume is still in use.

---

### Post by herbster on 2010-03-08
> **bodhi.zazen said:**
> If there is nothing on it, simply reformat it.

From the error message I am guessing you need to unmount and deactivate the partitions / logical volumes. Along those lines, what is "stuff" ? do you have more then one logical volume ?.

the error messages are telling you your volume is still in use.

Thanks, I actually *just* saw with mount that it was still mounted to /srv/nfs4/stuff, and it wasn't showing up with fuser. Unmounted it to there and wiped the volume group, logical volume and the physical volumes, it's gone now :) Thanks.

---

