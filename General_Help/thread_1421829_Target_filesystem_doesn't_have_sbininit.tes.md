---
title: "Target filesystem doesn't have /sbin/init.tes"
date: 2010-03-04
forum: General Help
---

### Post by reg2117 on 2010-03-04
Ubuntu Forum Members,

Having trouble booting into Kubuntu originally installed with Wubi.

The system returns this error:

```
mount: mounting /dev/loop0 on /root failed: Device or resource busy
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directoryisks
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.tes]
No init found. Try passing init= bootarg
```

This appears to be similar to the problem [[COLOR="Blue"]here[/COLOR]]("http://www.linuxquestions.org/questions/ubuntu-63/boot-failure-sbininit-missing-help-382491/"), [[COLOR="Blue"]here[/COLOR]]("http://kubuntuforums.net/forums/index.php?topic=3096976.0"), [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=223773") and [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1311184"). When I try:

```
sudo fdisk -l
```

I get the following:

```

   Device Boot      Start         End      Blocks   ID  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        4864    39029917+   7  HPFS/NTFS

```

I tried fsck on the file system and with the live cd disk check. Don't know where to go from here to get things running again.

I would be happy to either get the system up again or access some of the files for backup with the live cd.

Any help would be appreciated.

---

### Post by reg2117 on 2010-03-04
Found the solution here:
[[COLOR="Blue"]WubiGuide[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?")

From the live cd Konsole:
```
sudo mkdir /win
sudo mount /dev/sda1 /win
sudo mkdir /vdisk
sudo fsck /win/ubuntu/disks/root.disk
```

---

