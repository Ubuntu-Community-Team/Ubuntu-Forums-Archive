---
title: "Disk info: FS, mount point, partition name, size"
date: 2010-05-31
forum: General Help
---

### Post by UranUtan on 2010-05-31
Hi,

What is the command that list the complete disk layout: the mount points, partition type, file system, size? For example, I would like to see:

```
/dev/sda5   10GB ext2 /      primary bootable
/dev/sda6  145GB ext4 /home  extended
```

Very much like the GUI of System / Administration / System Monitor, Select "File System" tab. Is there a command line equivalence ?

Thanks in advance for any help.

---

### Post by sdennie on 2010-06-01
There are various commands that give this kind of information.  I would run all the following commands and see which one you prefer:

```

df
mount
cat /proc/mounts
blkid
sudo fdisk -l  #This is safe.  It's just a very low level read and so needs sudo.

```

---

### Post by UranUtan on 2010-06-02
Hi,

Thank you for your help. I had already tried, except for mount and proc/mount. Each of these commands gives a chunk of the information. I had to cross reference line by live via sometimes device name or UUID to complete all the info. It's rather tedious so finally I did the poor man version, looking at system monitor screen and write down the info.

It's surprising that since Linux existed, no one had felt the need to have these 4 info together in 1 single line. These are the basic info asked by Gparted when I created the partitions. I thought it would be easy to read these info back but it sounds like it's quite complicate.

---

