---
title: "Mount a second harddrive automatically"
date: 2010-02-23
forum: General Help
---

### Post by bigred1 on 2010-02-23
I have a second drive, with Windows and various stored files, on it.

I want it to auto-mount when I boot up Ubuntu, or when I click on its icon ("Local Disk"). However, I get a root password challenge, which is a bother.

Recently I reinstalled Karmic. Before that, the system did not give such a challenge. It must have had some special configuration setting.

How can I auto-mount? Can this be configured through the KDE GUI?

---

### Post by leg on 2010-02-23
You need to add a setting to the fstab file. Can't remember exactly how the line should look but if you open the file it should be fairly obvious.

---

### Post by joep-vd on 2010-02-23
I've found it not so trivial, but the following info was helpful for me: 

You have to put an extra line in /etc/fstab through some text editor. This line has some fairly basic settings, maybe 'default' will not work for you, then you have to search a bit for alternatives. 
What could go wrong: The mount point should have sufficient permissions (for example /media/music 

To get your device ID type ```
blkid
```

and to test if your setting worked, remount your fstab list: ```
sudo mount -a
```

---

### Post by plucky on 2010-02-23
> **bigred1 said:**
> I have a second drive, with Windows and various stored files, on it.

I want it to auto-mount when I boot up Ubuntu, or when I click on its icon ("Local Disk"). However, I get a root password challenge, which is a bother.

Recently I reinstalled Karmic. Before that, the system did not give such a challenge. It must have had some special configuration setting.

How can I auto-mount? Can this be configured through the KDE GUI?

```
sudo apt-get install ntfs-3g ntfs-config
```

Then go to **System > Administration > NTFS Configuration Tool** to open the GUI to mount your NTFS partitions.

Not sure if it will work for KDE but I think it should.

Good Luck

---

### Post by Detonate on 2010-02-23
Here is the line in my fstab that mounts my Windows partition perfectly with user privileges.  On my machine, Windows is on sda2.  You will have to create the directory /mnt/Windows by issuing the command ```
sudo mkdir /mnt/Windows
``` first.  then add this line to your fstab file ```
kdesudo kate /etc/fstab
``` and save it.  You will have to change the "sda2" in the line to the partition your windows is on.  Then run ```
sudo mount -a
``` to make sure it is works.  After that it will be mounted automatically with user privileges.

/dev/sda2 /mnt/Windows ntfs-3g uid=1000,gid=1000,locale=en_US.UTF-8 0 0

---

