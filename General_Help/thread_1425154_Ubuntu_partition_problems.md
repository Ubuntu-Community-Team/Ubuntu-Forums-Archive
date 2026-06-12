---
title: "Ubuntu partition problems"
date: 2010-03-08
forum: General Help
---

### Post by uShafee on 2010-03-08
Hai. while installing ubuntu i made two partitions and set two load points. 

/
/home/

but in ubuntu there is only one partition shown(filesystem).. what is going on?

---

### Post by WubiNoob on 2010-03-08
I don't think you need home as a mount point if you already have filesystem... Check the filesystem and see if home shows up there, then you don't need /home. I'm not exactly sure though. Hope this helps.

---

### Post by coffeecat on 2010-03-08
That's the way it works in Linux/Unix systems. The "filesystem" doesn't mean a partition - it means the whole system. You can have /boot, /usr, /etc, whatever set up on their own partitions if you want. So long as they are properly mounted they will show up in the filesystem.

In some enterprise/server settings they do have main system folders on separate partitions - sometimes on separate machines.

I think your question suggests you are still thinking in Windows ways. Windows and Linux/Unix are very different in the way they look at "drives", partitions and filesystems.

If you are worried about your partitions, have a look in System > Administration > System Monitor > File Systems tab. I think you'll find they're all there.

---

### Post by blueridgedog on 2010-03-08
If you think you made a partition that is not being mounted and used, you can verify with the output of the following in a terminal:

```
sudo fdisk -l
```

To list the partitions you have and 

```
mount
```

to display where they are mounted.

---

### Post by audiomick on 2010-03-08
A further word to what coffeecat posted. What all that means is that the filesystem mounts a separate partition exactly the same as it mounts any other folder. You cannot see whether a folder like /home is on a separate partition or not by just looking at the file system structure. You need a tool that looks at the HD setup, like fdisk, as blueridgedog suggested, or the Hard Drive tool in System> administration.

---

### Post by uShafee on 2010-03-09
I see.. i checked and it all looks okay. thanks.

---

