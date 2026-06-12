---
title: "Find device name of drives"
date: 2011-07-28
forum: General Help
---

### Post by Ghost_Mazal on 2011-07-28
Lo All ,

What command do I need to use to find the device name of drives , in particular an inserted USB drive that is not mounted yet ?

Everywhere I search tell me to do this: 

```
tail -f /var/log/messages
```

But that file doesn't exist.

Can someone help me please

---

### Post by sanderj on 2011-07-28
Why not use the GUI: System -> Administration -> Disk Utility. There you will see all the disks, and their partitions, including their names like /dev/sda1 and /dev/sr0

---

### Post by Ghost_Mazal on 2011-07-29
> **sanderj said:**
> Why not use the GUI: System -> Administration -> Disk Utility. There you will see all the disks, and their partitions, including their names like /dev/sda1 and /dev/sr0

I often work on server machines too so wanted a cli command that I can use no matter what the install is I am working on. While looking for something else I stumbled upon these two commands that do the trick.

```
sudo blkid
```

```
sudo lshw -C disk
```

---

### Post by mcduck on 2011-07-29
> **Ghost_Mazal said:**
> Lo All ,

What command do I need to use to find the device name of drives , in particular an inserted USB drive that is not mounted yet ?

Everywhere I search tell me to do this: 

```
tail -f /var/log/messages
```

But that file doesn't exist.

Can someone help me please
This works fine even on 11.04:
```
tail -f /var/log/syslog
```


You can also use commands like "sudo fdisk -l", "mount", "blkid" and probably countless amount of others. But tailing a log file is better than any other since it actually shows you information about the drive (or device) *even if it's not detected and mounted correctly*.

---

