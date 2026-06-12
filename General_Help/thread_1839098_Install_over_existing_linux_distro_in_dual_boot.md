---
title: "Install over existing linux distro in dual boot?"
date: 2011-09-04
forum: General Help
---

### Post by listerdl on 2011-09-04
Do u guys think if I install another distro over existing ubuntu partition, (i.e. ext4) grub2 will pick it up?

---

### Post by sum1nil on 2011-09-05
I know it will if it is another Ubuntu version. For example, I did a wipe/clean install of Oneiric over Natty (dual boot with Win7) and there were no problems with grub.

I have no idea if that would be so with a different version of linux. 
Sorry.

---

### Post by Duncan Williams on 2011-09-05
I would say, format the ext4 partition, install into it, the install should reset your grub...

---

### Post by listerdl on 2011-09-06
> **Duncan Williams said:**
> I would say, format the ext4 partition, install into it, the install should reset your grub...

Thanks...thats what I thought to but when I came to the install and select manual partition I select the ext4 partition (with existing ubuntu) the error reads:

"No root file system is defined. Please correct this from the partitioning menu"

Any idea what the cause could be here?

PS The dual boot seems to work perfectly...

---

### Post by Duncan Williams on 2011-09-07
Havn't done an instalation for a few months.
not sure offhand, someone else should be able to comment though.

---

