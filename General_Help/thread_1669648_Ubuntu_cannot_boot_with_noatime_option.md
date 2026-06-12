---
title: "Ubuntu cannot boot with noatime option"
date: 2011-01-18
forum: General Help
---

### Post by Peter_APIIT on 2011-01-18
Hello to all, 

i have added noatime option to /etc/fstab file but when i try to reboot, it cannot mount the file system. 

I try to erase the noatime option in /etc/fstab file but it does not allow for write because it is only a read only file system. 

How can i mount with write access which allow me to delete the noatime option in /etc/fstab. 

Thanks. 

Please help.

---

### Post by Peter_APIIT on 2011-01-19
My /etc/fstab looks like this : 

/dev/sda3
UUID = somenumber / ext3 relatimeerrors=remount-ro,noatime 0 1
/devsda6
UUID = somenumber none swap sw 0 0

Please help.

---

### Post by efflandt on 2011-01-19
How did you add it?  Mount options are a comma separated list, not words with spaces.

You can fix it if you boot an install CD or iso on USB to a live system if you know how to mount whatever is normally your "/" partition of your installed Ubuntu system.

You can probably pick that partition in Places, the ls /media to see what it is called (typically by its UUID unless it have a partition label). The cd /media/label_or_UUID/etc, then **sudo nano fstab**

---

### Post by dcstar on 2011-01-20
> **Peter_APIIT said:**
> My /etc/fstab looks like this : 

/dev/sda3
UUID = somenumber / ext3 relatimeerrors=remount-ro,noatime 0 1
/devsda6
UUID = somenumber none swap sw 0 0

Please help.

This is the line on my system that works fine:

```
UUID=adaf9c80-1d4e-40d8-a7f6-171f6523c8e1	/		ext4		errors=remount-ro,noatime		0  1
```

Please note that you need **all** the delimiters.

---

