---
title: "USB Disk Permission Problem"
date: 2009-12-03
forum: General Help
---

### Post by n4lbl on 2009-12-03
I have an ext4 partition on a USB drive that I can't access.  I get permission denied messages.  Having found some appropriate hits here in the forum I tried the following in a terminal session.  

n4lbl@bottom-fish:~$ sudo chown -R n4lbl:n4lbl /dev/sdb2
[sudo] password for n4lbl: 
n4lbl@bottom-fish:~$ sudo chmod -R 777 /dev/sdb2
n4lbl@bottom-fish:~$ 


The symptoms remain.  I hope that I haven't dived in too quickly and missed something.

---

### Post by greg963 on 2009-12-03
/dev/sdbX is the device node, so it is basically a mapping of the hardware that tells the kernel where to find things (not a very good explanation but hopefully sufficent), you need to figure out where the usb drive is mounted.

```

greg@squizz:~$ mount | grep '^/dev'
/dev/mapper/lv0-root on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda1 on /boot type ext3 (rw,relatime)
/dev/mapper/lv0-home on /home type ext3 (rw,relatime)
/dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1001,utf8,umask=077,flush)
greg@squizz:~$ 

```

So int the above /dev/sdd1 is mounted at /media/disk, so to change the permissions I would:
```

sudo chmod -R 755 /media/disk

```

---

### Post by n4lbl on 2009-12-03
Thanks Greg.  the output is:

n4lbl@bottom-fish:~$ mount | grep '^/dev'
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb2 on /media/minke type ext4 (rw,nosuid,nodev,uhelper=hal)
n4lbl@bottom-fish:~$ /dev/mapper/lv0-root on / type ext3 (rw,relatime,errors=remount-ro)
bash: syntax error near unexpected token `('
n4lbl@bottom-fish:~$ /dev/sda1 on /boot type ext3 (rw,relatime)
bash: syntax error near unexpected token `('
n4lbl@bottom-fish:~$ /dev/mapper/lv0-home on /home type ext3 (rw,relatime)
bash: syntax error near unexpected token `('
n4lbl@bottom-fish:~$ /dev/sdd1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1001,utf8,umask=077,flush)
bash: syntax error near unexpected token `('
n4lbl@bottom-fish:~$ 

I don't know what to do with that.  I think that it is saying that I did want to use /dev/sdb2

---

### Post by n4lbl on 2009-12-03
Greg:

I've been told that I hit the 'report abuse' button (right above 'new reply').  I don't know how to undo it.

thanx,,,

---

### Post by greg963 on 2009-12-04
> 
Thanks Greg. the output is:

n4lbl@bottom-fish:~$ mount | grep '^/dev'
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1 000,utf8,umask=077,flush)
/dev/sdb2 on /media/minke type ext4 (rw,nosuid,nodev,uhelper=hal)


n4lbl,
Based on the output you supplied above above /dev/sdb2 is mounted on /media/minke, so to change the permissions:

```

sudo chown -R n4lbl:n4lbl /media/minke
sudo chmod 755 /media/minke 

```

---

### Post by n4lbl on 2009-12-04
Many thanks Greg.  Now, on to the next problem!!

I'm sorry over the confusion I created with hitting the abuse button instead of the new reply button.

Alan

---

