---
title: "How to change file permissions of host in Wubi?"
date: 2011-01-01
forum: General Help
---

### Post by allencch on 2011-01-01
I would like to do web development using Wubi, where the file directory also accessible by Windows 7. Therefore, I am using the directories within /host.

I need to change the file permission of the htdocs so that the folder can be accessible through HTTP. However, when I use "chmod", there is no effect towards the folder.

May I know what is the solution, so that I can chmod the files within /host using Wubi?

---

### Post by WorMzy on 2011-01-01
NTFS filesystems do not support Linux file permissions. There is a way to set the permissions on NTFS partitions, but it needs to be done at mount time, and I'm not sure that's possible with Wubi installations.

Check your /etc/fstab file, if it has an entry for /host, then it may be possible. This tutorial should help you get things the way you want them:
[[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

Please note that if there is an entry for /host, I can't guarantee that modifying it won't cause Ubuntu to stop booting. Edit it at your own discretion.

---

### Post by allencch on 2011-01-01
WorMzy, thanks for your quick reply. The following is my fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0


Meaning that one of the method is mount the /host file with the options to enable the permission? I will try it. Thank you very much.

---

### Post by allencch on 2011-01-01
I solved the problem. Just need to change the /etc/default/grub with, at a line, modified to:
```
GRUB_CMDLINE_LINUX_DEFAULT="rootflags=umask=002,uid=1000,gid=1000 quiet splash"

```
Thanks.

---

### Post by Kenned999 on 2011-02-07
Hi there.

I have the same problem as you. I inserting that line you suggested in /etc/default/grub and rebooted, but a "sudo chown ......" doesnt change anything when used on files in  /host/.

Have you done anything else to make this work? 

Sorry for taking up an old topic but it is really annoying not to be able to change permission on files in /host/ :)

Regards
Kenneth

---

### Post by WorMzy on 2011-02-07
No matter what you do, chown, chmod and chgrp will not work on NTFS partitions (which is what /host is). What allencch has done by adding that line to the grub config file (and then running update grub) is made it so that Ubuntu believes that everything on /host is owned by him and the permissions are set to 775. You can't change the permissions/ownership on individual files and folders in /host, because NTFS doesn't support the permissions in the first place.

---

