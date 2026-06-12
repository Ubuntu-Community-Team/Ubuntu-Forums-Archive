---
title: "upgraded to lucid..mounting errors, now got worst. Anyway to reset them?"
date: 2010-05-01
forum: General Help
---

### Post by ram130 on 2010-05-01
I upgraded from 9.10 to 10.04. Everything went fine except for some driver errors which were later fixed. When booting I'm getting error mounting 0. Pressing S allows it to boot. I never had this error with 9.04 so I don't know what happen. I have one swap partition, ext4, windows and regular partition. 

I made the problem worst. In the post I found somewhere around here after googling. It said try binding /tmp /dev  and mounting the root to /mnt. I'm not sure exactly what it said. Anyway after rebooting, I now get the above error again but with /tmp /dev and so on included to the point  where it says you can wait, press S to skip or M for recovery. Trying both equals no more booting. Help someone, please.:confused::confused:

---

### Post by P4man on 2010-05-01
Oh dear. You messed up good there!

Can you boot a livecd?

---

### Post by ram130 on 2010-05-01
> **P4man said:**
> Oh dear. You messed up good there!

Can you boot a livecd?

I know right, and its my moms pc. Trying hard not to loose anything. I did a fresh installed on my laptop and it went smooth except the X Server crashed on start up. Same thing happen with my moms desktop, I guess something funky is up with the ATi drivers since I did an upgrade on the desktop and a clean install on the laptop. Both with ATI cards.

To answer, yes I can boot the live cd just fine.

---

### Post by ram130 on 2010-05-01
IS there no way I can undo the changes or unbind /tmp /dev?? At least I can have  a boot able system again..:( ..help

---

### Post by prshah on 2010-05-01
> **ram130 said:**
> It said try binding /tmp /dev  and mounting the root to /mnt. I'm not sure exactly what it said.

The solution to your initial problem is to simply comment out the entries in the /etc/fstab. However, I don't know what you have done now; so I don't know if it will work for you. No harm in trying:

Enter maintenance mode, then edit your /etc/fstab```
nano /etc/fstab
``` then comment out all lines not related to your main linux partition. Comment out lines for swap, windows and regular (?) partition.

Save, exit and reboot. If it works, leave the fstab as it is. If it doesn't uncomment the lines, save and try something else.

Hope this helps,

---

### Post by P4man on 2010-05-01
How did you "bind it" ? do you have a link to the instructions you tried to follow? You mention mounting root in /mnt.. that sounds like something someone told you to do from a **livecd** to "boot" (actually: chroot) the installation on your harddisk?

Anyway, yes you can probably undo what you did, but it would help to know what you did. If you cant give details, start by booting the livecd, and browse your harddisk. Look for /etc/fstab on your harddisk (so actual path would be something like /media/somereferencetoyourharddisk/etc/fstab)

paste the contents here. Is that something you remember changing?

---

### Post by ram130 on 2010-05-01
I manage to get the system to boot back up after pressing S by removing the entry in my fstab.

> :
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda3 during installation
**UUID=8e7cae7b-970b-4f7e-8d8c-410f3613877d / ext4 relatime,errors=remount-ro 0 1**
sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 

When its enable I get 3 errors mounting and at the last one it says /tmp is not ready or present, try waiting. Removing the entry from fstab causes only 1 error mounting "0". Using the M option I see mountall is saying invalid option "#" unable to mount. I only have one main linux partition so I don't know what happen. Any other info you guys need since I can boot into system now? Just need to get rid of these mount errors...:(

---

