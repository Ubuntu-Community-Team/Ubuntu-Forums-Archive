---
title: "Harddisk not mounted anymore after reboot"
date: 2009-12-20
forum: General Help
---

### Post by Zilioum on 2009-12-20
Today I installed the ubuntu server edition onto my mediaserver, which previously ran on the ubuntu desktop version. After installing the server edition onto the primary harddisk, I wanted to add my secondary disk on which I store all the movies etc. I created a mountpoint with "sudo mkdir /media/mediadisk" and then edited my fstab file to look like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3fe9f948-5806-43fd-8e6d-168fa2a891b5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=37fe898d-7272-46c0-8b75-2f1cf69b66ca none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/mediadisk ext3 defaults 0 2

```

I then used "sudo mount -a" and everything was fine. The second harddrive was mounted under "/media/mediadisk/". I then used "sudo chown -R USERNAME:USERNAME /media/mediadisk" to make it writable (following [this tutorial]("https://help.ubuntu.com/community/InstallingANewHardDrive#Automatic%20Mount%20At%20Boot"))
 After rebooting the server, it didnt show up anymore. When running "sudo mount -a" I get ```
mount: /dev/sdb1 already mounted or /media/mediadisk busy

```

Again: If I mount it the first time, it works. After rebooting the disk is invisible and when using "sudo mount -a" I get the above error message.

Cheers

---

### Post by Zilioum on 2009-12-20
All of a sudden it works, weird....
If anyone knows what the problem might have been, I'd still be happy to hear your ideas.

---

