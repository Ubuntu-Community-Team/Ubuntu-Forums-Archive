---
title: "Making disks mount forever."
date: 2010-01-26
forum: General Help
---

### Post by Cityscape on 2010-01-26
Hi, I have a computer with XP & Ubuntu dual-boot. My arrangement is like this:
Physical hard drive #1, (NTFS XP partition, ext3 Ubuntu partition)
Physical hard drive #2, (NTFS documents partition)

The Ubuntu partition is always mounted, but the other 2 have to be mounted every-time I boot up. How can I have these other 2 partition always be mounted?

---

### Post by t4thfavor on 2010-01-26
Lookup how to add an entry to /etc/fstab, and you can have them mount where you want every boot. It's really easy if you just know where to start.

---

### Post by michael37 on 2010-01-26
[Community guide to fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by Cityscape on 2010-02-23
> **michael37 said:**
> [Community guide to fstab]("https://help.ubuntu.com/community/Fstab")
Was too complicated. Can someone give me a simpler how-to?

---

### Post by dabl on 2010-02-23
First, make a backup copy of /etc/fstab:

```
sudo cp /etc/fstab /etc/fstab_bak
```


1. You need a mount point for each of the other two partitions. So ```
sudo mkdir /mnt/XP
sudo mdkir /mnt/WINDOCS
```

2. You need to know the UUID numbers of the two partitions that you want mounted at boot.  ```
sudo blkid
```

Note the numbers and their associated /dev/sd*xn* partition numbers.

3. You need to edit your /etc/fstab file to have it mount the devices to the mount points at boot time:

```
sudo gedit /etc/fstab
```

With the file open in the editor, add these lines, ideally below the line that mounts the "/" filesystem, and above the CD ROM mount line:

UUID={*first number here*} /mnt/XP  ntfs-3g defaults   0  2
UUID={*other number here*} /mnt/WINDOCS  ntfs-3g defaults   0  2

Do not make any typos, and if you copy and paste the UUID numbers, make sure to omit the apostrophe!

Do a "File > Save" when you are finished, and then reboot your system, or you could just issue ```
sudo mount -a
```  in the console.

If anything broke or seems wrong, you can get back to your present state by restoring the backed up /etc/fstab file:

```
sudo mv /etc/fstab_bak /etc/fstab
```

---

