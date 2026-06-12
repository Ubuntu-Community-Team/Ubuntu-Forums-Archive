---
title: "Mounting a hard drive in terminal"
date: 2011-03-15
forum: General Help
---

### Post by nkae100 on 2011-03-15
I want to know how I can mount "/dev/sda3" from terminal. 
 
 
I execute "sudo mount /dev/sda3" in terminal and get the following error: 
 
mount: can't find /dev/sda3 in /etc/fstab or /etc/mtab 
 
 
I am able to mount it in Disk Utility (the application included in Ubuntu 10.04 LTS). It mounts at "/media/AC70B11E70B0F066". 
 
Once its mounted, I can execute the command "sudo umount /dev/sda3" in terminal fine. 
 
 
Anyone know whats going on? 
 
 
I need this volume mounted at boot time and plan on achieving this by inserting the magic command into "rc.local".

---

### Post by rubylaser on 2011-03-15
You need to set a mount point to mount the partition, like this...
```
sudo mount /dev/sda3 /mnt/
```

This would make it mounted at /mnt.  The better way to get this to be automounted every time you boot is to add the partition to /etc/fstab.

First run
```
blkid /dev/sda3
``` In a terminal.  It should output something like this...
```
/dev/sda3: UUID="b46c33d1-9af5-4636-aed3-90a824f52b32" TYPE="ext4"
```

Then you take that UUID, and add it to your /etc/fstab
```
UUID=b46c33d1-9af5-4636-aed3-90a824f52b32 /mnt               ext4    errors=remount-ro 0       2
```

Hope that helps. If you want to make the partition mount somewhere else, just change the /mnt to whatever mount point you want. After making these changes, you can mount the drive with, 
```
mount -a
```

---

