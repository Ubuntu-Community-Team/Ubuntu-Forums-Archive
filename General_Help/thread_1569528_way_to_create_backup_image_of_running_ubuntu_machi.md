---
title: "way to create backup image of running ubuntu machine?"
date: 2010-09-06
forum: General Help
---

### Post by dondartagnan on 2010-09-06
Hey!

I would really appreciate any advice on the situation. We have an Ubuntu 10.04 box that's running a bunch of client websites. We currently have no good backups of the machine, and are worried if the thing goes down. At that point we would be screwed. We are hoping to find an imaging solution so we could backup the machine while it's running. I've run into quite a few solutions that would work if we take down the machine and unmount the drive, but we are hoping for something that will create an image while it's running. We would rather not have any downtime. The file system is ext4. If this is possible, and anyone could point me in the right direction it would be much appreciated.

Thanks in advance!!

---

### Post by Dayofswords on 2010-09-06
i'm no expert, but i'm guessing you'll run into rsync at some point

also could some link me to somewhere explaining how you can run multiple websites from one server?

---

### Post by dcstar on 2010-09-07
> **Dayofswords said:**
> 
.........
also could some link me to somewhere explaining how you can run multiple websites from one server?

No, but if you search for http-headers on the Internet you should find plenty of things.

---

### Post by TNT1 on 2010-09-07
> **dondartagnan said:**
> Hey!

I would really appreciate any advice on the situation. We have an Ubuntu 10.04 box that's running a bunch of client websites. We currently have no good backups of the machine, and are worried if the thing goes down. At that point we would be screwed. We are hoping to find an imaging solution so we could backup the machine while it's running. I've run into quite a few solutions that would work if we take down the machine and unmount the drive, but we are hoping for something that will create an image while it's running. We would rather not have any downtime. The file system is ext4. If this is possible, and anyone could point me in the right direction it would be much appreciated.

Thanks in advance!!

Remastersys?

---

### Post by dcstar on 2010-09-07
> **dondartagnan said:**
> Hey!

I would really appreciate any advice on the situation. We have an Ubuntu 10.04 box that's running a bunch of client websites. We currently have no good backups of the machine, and are worried if the thing goes down. At that point we would be screwed. We are hoping to find an imaging solution so we could backup the machine while it's running. I've run into quite a few solutions that would work if we take down the machine and unmount the drive, but we are hoping for something that will create an image while it's running. We would rather not have any downtime. The file system is ext4. If this is possible, and anyone could point me in the right direction it would be much appreciated.


If you have an external eSATA disk as part of a RAID-1 array then that would hold a real-time image of the running system in a portable device.

---

### Post by Irony on 2010-09-07
This works for me from a live system to an external usb drive;

```
sudo cp -axv /. /media/nameoffolder/.
```

If I mess up my system I format it then use the same method to copy it back.

---

### Post by Sabir_101 on 2010-09-07
You could use:

```
dpkg --get-selections > packages.txt
```

To backup which packages are installed on your server, then use:

```
apt-get update
dpkg --set-selections < packages.txt
apt-get upgrade
```

To reinstall them on a fresh machine if it goes down.

Irony's "cp -axv" method can preserve your configuration files for you which should, in total, make a full system backup. I realise its not disk imaging but its an easy solution.

---

