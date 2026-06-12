---
title: "Automount of partitions not working"
date: 2011-08-09
forum: General Help
---

### Post by sidewalkcynic on 2011-08-09
I recently installed UbuntuStudio. I have five partitions on the harddrive that I like to have automounted, because they contain a lot of virtual links between each other, and if the links are to an unmounted partition they appear to be dead links and do not mount the partition when selected.

I have tried every combination of the media mount options in gconf-editor, but nothing works.

If I have to edit etc/fstab, what do I need?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=302c4a5e-fb38-4aab-9b84-f57385133c12 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=2dcec013-41cb-4e3f-9174-a694afa8673b /home           ext4    defaults        0       2
# /opt was on /dev/sda3 during installation
UUID=b4898ff9-0d78-4eff-a900-65daf8eddbf7 /opt            ext4    defaults        0       2
# /usr was on /dev/sda2 during installation
UUID=54eaa015-4c2c-470d-9a61-830c13b4908d /usr            ext4    defaults        0       2
```

---

### Post by Kira_Belka on 2011-08-09
ls /dev/disk/by-id or by-uuid :)

mmmm.. you need to know name of drivers and partitions.. and filesystem type.. also wisheable for you mount point for each partition..that's all

---

### Post by sidewalkcynic on 2011-08-09
Well, those identifiers do not seem to be in a recognizable order in the directories, so could you help me little further?

---

### Post by Morbius1 on 2011-08-09
Please post the output of the following commands:
```
sudo blkid -c /dev/null
```
```
mount
```

---

