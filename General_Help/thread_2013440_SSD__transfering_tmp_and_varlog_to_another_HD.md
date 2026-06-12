---
title: "SSD : transfering /tmp and /var/log to another HD"
date: 2012-06-30
forum: General Help
---

### Post by LeftFoot on 2012-06-30
Hi there,

I intend to transfer /tmp and /var/log to another hard drive. 
I saw that you can mount them in memory with tmpfs but I don't want to do that (I have plenty of HD space and I love to save RAM :D )

I have 2 questions about this :

1- What space should I book ? 5GB should be more than enough right ?

2-How to set up /var/log in the second HD ?
During the installation, you just create a partition and mount it as /var/log ?
It seems obvious but this feel odd to me to create a mounting point that is not directly under /  :-k

Thx for any help !

LeftFoot

---

### Post by matt_symes on 2012-07-05
Hi

> **LeftFoot said:**
> Hi there,

I intend to transfer /tmp and /var/log to another hard drive. 
I saw that you can mount them in memory with tmpfs but I don't want to do that (I have plenty of HD space and I love to save RAM :D )

I have 2 questions about this :

1- What space should I book ? 5GB should be more than enough right ?

5GB should be more than enough.

> 
2-How to set up /var/log in the second HD ?
During the installation, you just create a partition and mount it as /var/log ?
It seems obvious but this feel odd to me to create a mounting point that is not directly under /  :-kYou can create a mount point anywhere so don't worry about that. Removable media get mounted under /media at the moment.

```

[matthew@matthew-aspire7450 ~]$ mount | grep "^/"
/dev/sda7 on / type ext4 (rw,relatime,seclabel,data=ordered)
/dev/sda10 on /home/matthew/storage type ext4 (rw,relatime,seclabel,data=ordered)
/dev/sda1 on /mnt type ext4 (rw,relatime,seclabel,data=ordered)
[matthew@matthew-aspire7450 ~]$
```At the moment i have the storage partition mounted under /home/matthew/storage and i have sda1 mounted under /mnt (this last one is just temporary though).

Check out mount with the --bind option to mount /var/log. Add to fstab. I think that may do what you need.

If you need direction then post back.

Kind regards

---

### Post by SlugSlug on 2012-07-05
Just a note on this.. I've read ina few places most new SSD's last as long as HDD's in regards to writes, so there is no real point in making different mount points for /var/logs and /tmp

---

