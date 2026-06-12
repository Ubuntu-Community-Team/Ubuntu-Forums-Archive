---
title: "ext4 external drive doesn't work for second user"
date: 2010-05-05
forum: General Help
---

### Post by tgoren on 2010-05-05
Hi all,
First post!
I did a clean install of ubuntu 10.4 on my thinkpad t61 and tried using my two seagate external drives, all fine. One of the drives is ntfs and the other is ext4. But when I make a second user, admin or not, the second user can see both drives but cannot browse to the ext4 drive (error message: Could not enter folder /media/ext4m.) Whether the drive is mounted or not by the first user doesn't matter, unplugging and replugging doesn't help, adding a third user doesn't matter, whether the first user is logged in or not doesn't matter, and manually mounting the drive to a different folder had the same effect (but I can't guarantee I did that right). The ntfs drive works fine for any and all users, as expected.
Help would be appreciated!
with thanks
Tgoren

---

### Post by warfacegod on 2010-05-05
Try going to Users & Groups and adding the user it doesn't work for to the user group it does work for. If that doesn't work try adding them to the root usergroup.

---

### Post by WorMzy on 2010-05-05
Can you post the contents of /etc/mtab please.

---

### Post by tgoren on 2010-05-06
Thanks for the replies! No luck though.

@warfacegod, I tried both but didn't help. Tried full restarting in between, and tried having only new_user logged on.

@WorMzy: here's /etc/mtab:
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/ext4m ext4 rw,nosuid,nodev,uhelper=hal 0 0
/dev/sdc1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,uid=1002,utf8,shortname=mixed,flush 0 0

---

