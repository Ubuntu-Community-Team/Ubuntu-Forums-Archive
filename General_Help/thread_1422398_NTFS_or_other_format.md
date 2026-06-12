---
title: "NTFS or other format?"
date: 2010-03-05
forum: General Help
---

### Post by quez69 on 2010-03-05
Newbie here. I am installing ubuntu on my laptop, to a new drive. It is currently formatted FAT. I will be primarily working in a windows network environment. should I format the drive NTFS? for sharing purposes or leave it like it is or format it some other method.

Thx

---

### Post by TitanusEramius on 2010-03-05
It doesn't matter what the harddisk is formatted in when you are talking networking. If you only install Ubuntu on your laptop, you should go with the standard filesystem for Ubuntu (it's ext3). The Ubuntu installation-program will suggest this by default.

Besides, Ubuntu won't work on NTFS, so you will only need that if you install both Linux and Windows on the same machine.

---

### Post by jmichelsen on 2010-03-05
TitanusEramius is correct that you will need to format with a linux based file system to run linux. Ext4 is actually the new standard, though you can choose between a plethora of others during install (reiserfs, ext3, ext2, etc.)

Ext4 is your best choice for the standard install and I won't go into the others. As far as the network goes, you will have all the tools you need to share to and from the network.

Samba can be used to create shares accessible by Windows machines, and cifs or NFS can be used in conjunction with mount to add windows shares to the linux box.

Here's an example of cifs usage

```
sudo mount -t cifs //windowshost/shareddir /mount/point -o username=username
```

username will be the username on the windows box, and the mount point is something you choose. The command will prompt for your sudo password as well as the windows host password.

and NFS:

```
sudo mount windowshost:/shared/dir /mount/point
```

anyway, hope this helps

---

