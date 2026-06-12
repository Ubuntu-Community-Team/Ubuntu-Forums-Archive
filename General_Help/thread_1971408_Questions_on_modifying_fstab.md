---
title: "Questions on modifying fstab"
date: 2012-05-02
forum: General Help
---

### Post by cashmank on 2012-05-02
My fstab file seems to be differently formatted than others I've seen, and I'm trying to add noatime, discard (for TRIM), and nodiratime to it. I've done this in the past, but I'm not sure it was correct.

This is my fstab file:

> 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/cashmank-root /               ext4    errors=remount-ro,user_xattr 0       1
# /boot was on /dev/sdb1 during installation
UUID=90c6308d-89f3-4fe7-bf79-584e13e2ae04 /boot           ext2    defaults        0       2
/dev/mapper/cashmank-swap_1 none            swap    sw              0       0



And this is how I think I should edit it:

> 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/cashmank-root /               ext4 [COLOR=Blue]noatime,discard,nodiratime[/COLOR] errors=remount-ro,user_xattr 0       1
# /boot was on /dev/sdb1 during installation
UUID=90c6308d-89f3-4fe7-bf79-584e13e2ae04 /boot           ext2 [COLOR=Blue]noatime,discard,nodiratime[/COLOR] defaults        0       2
/dev/mapper/cashmank-swap_1 none            swap    sw              0       0



Is this correct?

---

### Post by LewisTM on 2012-05-02
[FONT="Courier New"]nodiratime[/FONT] is implicit in the [FONT="Courier New"]noatime[/FONT] statement.
You missed a comma before your first [FONT="Courier New"]errors=remount-ro[/FONT].
The rest, TRIM and discard business, I leave to others with more experience.

Cheers!

---

### Post by JRV on 2012-05-02
Is this an SSD or a mechanical drive?
Trim (discard) is for SSDs.
Noatime is used mostly on SSDs to minimize writes, but is might speed up a mechanical drive slightly,

---

### Post by cashmank on 2012-05-02
> **JRV said:**
> Is this an SSD or a mechanical drive?
Trim (discard) is for SSDs.
Noatime is used mostly on SSDs to minimize writes, but is might speed up a mechanical drive slightly,

It's a solid-state USB drive.

---

### Post by cashmank on 2012-05-03
Would this be correct?

> 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/cashmank-root /               ext4 [COLOR=Blue]noatime,discard,[/COLOR]errors=remount-ro,user_xattr 0       1
# /boot was on /dev/sdb1 during installation
UUID=90c6308d-89f3-4fe7-bf79-584e13e2ae04 /boot           ext2 [COLOR=Blue]noatime,discard,[/COLOR]defaults        0       2
/dev/mapper/cashmank-swap_1 none            swap    sw              0       0



---

### Post by JRV on 2012-05-03
Looks good to me.

---

### Post by cashmank on 2012-05-03
So I tried out that fstab configuration and the /boot partition was unable to be mounted when entering my encryption key (the system is encrypted with LUKS).

So I guess my question is:

I have four separate places where I could add the options, and where should they be added?

1. proc            /proc           proc    nodev,noexec,nosuid 0       0

2. /dev/mapper/cashmank-root /               ext4 errors=remount-ro,user_xattr 0       1

3. UUID=90c6308d-89f3-4fe7-bf79-584e13e2ae04 /boot           ext2 defaults        0       2

4. /dev/mapper/cashmank-swap_1 none            swap    sw              0       0

For 1., I'm not sure what that partition is.

On 2., it seems like the options are working.

On 3., the options didn't work (unless I added them incorrectly).

For 4., in my limited experience, I don't think it makes sense to add options to the swap partition.

---

### Post by JRV on 2012-05-03
I'm sorry if any advice I gave was wrong, You never mentioned anything about encryption, and I don't know anything about it.

---

### Post by Cheesemill on 2012-05-03
There is no point in using the discard flag on an encrypted drive.

In fact even if you do try to use it dm-crypt doesn't support TRIM anyway so the option is simply ignored.

---

### Post by cashmank on 2012-05-04
> **JRV said:**
> I'm sorry if any advice I gave was wrong, You never mentioned anything about encryption, and I don't know anything about it.

No worries, it wasn't a big deal. I should have mentioned it was encrypted.

---

