---
title: "USB Drives change /dev/sd?"
date: 2010-09-21
forum: General Help
---

### Post by slamMaster on 2010-09-21
Hello list,

I run an Ubuntu server at home that has two usb drives permanently plugged into it.  I've been toying with the setup recently, and rebooting a lot, and I've been running into trouble with auto-mounting the two drives.  I have a script that runs at startup that mounts the two drives, but it's problem is that the letters the drives are assigned to keep changing, which I think is due to the fact that they're plugged into a USB extender.  For example, the scripts run

mount /dev/sdb1 /media/LACIE 
mount /dev/sdc1 /media/myBook

But my problem is that LACIE isn't consistently assigned sdb1, sometimes it's at sdd1 or sdc1, and the same with the myBook.  Is there a way to run the mount command based on the usb id or something similar?

---

### Post by slamMaster on 2010-09-21
You know how explaining your problem also solves it for you?

You can mount the drives using their LABELS with the -L option.  To determine the labels, type

```
sudo blkid
```

Which produced the following:
```

UUID="cea5f078-2ff1-47fd-bf47-8ce50d35f9f6" TYPE="swap" 
/dev/sdb1: LABEL="LACIE" UUID="6853-5BA9" TYPE="vfat" 
/dev/sdd1: LABEL="myBook" UUID="5429fec6-1028-436d-a080-7af034e04358" TYPE="ext3" 

```

So I can replace the devices with the LABELS

```

mount -L LACIE /media/LACIE
mount -L myBook /media/myBook 

```

---

### Post by lmarmisa on 2010-09-21
Other option is to use the mount command with the -U option (the partition to mount is defined by its UUID):

> 
mount -U "6853-5BA9" /media/LACIE
mount -U  "5429fec6-1028-436d-a080-7af034e04358" /media/myBook


---

