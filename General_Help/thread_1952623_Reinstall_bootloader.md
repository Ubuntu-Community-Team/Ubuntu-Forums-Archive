---
title: "Reinstall bootloader"
date: 2012-04-04
forum: General Help
---

### Post by petermg on 2012-04-04
Two partitions, first is windows XP, second Ubuntu 11.10.  When trying to boot I was getting 
```
GRUB Loading stage1.5.

GRUB loadin, please wait...
Error 2
```

So I did "fdisk /mbr" and now I can boot into windows XP on the first partition, but how can I install the UBUNTU bootloader so that I can boot into either Windows or Ubuntu?

---

### Post by TeoBigusGeekus on 2012-04-04
[There]("https://help.ubuntu.com/community/Grub2#ChRoot") you go.

---

### Post by petermg on 2012-04-04
At step SIX I get the following error:

```
fuse: failed to access mountpoint /dev/boot: input/output
```

:confused:

---

### Post by TeoBigusGeekus on 2012-04-05
Well, do you have a separate /boot partition?
This step is only required in that case.

---

### Post by petermg on 2012-04-05
> **TeoBigusGeekus said:**
> Well, do you have a separate /boot partition?
This step is only required in that case.

Yes, I do.  I have dual boot, first partition is Windows XP.

---

### Post by TeoBigusGeekus on 2012-04-05
Are you sure?
I mean, when you first installed ubuntu, did you specify a separate /boot partition along with / (root) and /home?

---

### Post by petermg on 2012-04-05
I know that my windows boot partition is /dev/sda1 and my Linux partition is /dev/sda5.

---

### Post by TeoBigusGeekus on 2012-04-05
> **petermg said:**
> I know that my windows boot partition is /dev/sda1 and my Linux partition is /dev/sda5.

That has nothing to do with a separate /boot partition.
When installing Ubuntu (or any linux distro), you can specify a separate partition for a lot of system folders: / (obviously), /home/, /var/, /boot/, /bin/, etc.

You DON'T have a separate /boot partition, you can carry on with the guide.

---

### Post by petermg on 2012-04-05
> **TeoBigusGeekus said:**
> That has nothing to do with a separate /boot partition.
When installing Ubuntu (or any linux distro), you can specify a separate partition for a lot of system folders: / (obviously), /home/, /var/, /boot/, /bin/, etc.

You DON'T have a separate /boot partition, you can carry on with the guide.

AWESOME!!! Will try that now!! :D

---

### Post by petermg on 2012-04-05
> **TeoBigusGeekus said:**
> That has nothing to do with a separate /boot partition.
When installing Ubuntu (or any linux distro), you can specify a separate partition for a lot of system folders: / (obviously), /home/, /var/, /boot/, /bin/, etc.

You DON'T have a separate /boot partition, you can carry on with the guide.

Ok, when I run this command:
```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
```

I get

```
mount: /dev: can't read superblock
mount: /dev/pts: can't read superblock
mount: /sys: can't read superblock
```

If I proceed to the next command anyways, which is
```
sudo chroot /mnt
```
I get
```
bash: /home/ubuntu/.bashrc: Input/output error
```
:confused:

---

### Post by TeoBigusGeekus on 2012-04-05
> **petermg said:**
> 
```
mount: /dev: can't read superblock
mount: /dev/pts: can't read superblock
mount: /sys: can't read superblock
```


Corrupt drive perhaps?
Boot up with the live cd and give
```
sudo fsck /dev/sdx
```
where /dev/sdx is your linux partitions.

---

### Post by petermg on 2012-04-07
> **TeoBigusGeekus said:**
> Corrupt drive perhaps?
Boot up with the live cd and give
```
sudo fsck /dev/sdx
```
where /dev/sdx is your linux partitions.

I think my linux partitions are hosed.  I attached it to a USB connected converter and the files came up with # symbols in front of them.  Think I will just consider the files lost and redo that partition/Ubuntu install.  Unless anyone knows what all the #'s in front the strange file names means.

---

