---
title: "moving /usr to another disk"
date: 2010-05-29
forum: General Help
---

### Post by deepesh on 2010-05-29
Hi,

I have one hard disk with a large partition (80GB... ok not that large) and number of small ones (~10GB). I usually install new versions of *x*buntu on small ones and manually move /usr to large disk (sudo cp --preserve=all -r /usr /media/disk/usr_xyz) and just have symbolic link to it (/usr -> /usr/media/disk/usr_xyz).
This system was working until I tried it on 10.04 (ubuntu/kubuntu both). Once usr is moved to another partition, wireless network stops connecting. It seems to have something to do with apparmor. Disabling apparmor for dhclient seems to make it work again. I tried creating an alias in /etc/apparmor.d/tunables/alias for /usr/ -> /media/disk/usr_xyz/, but it doesn't work.

Disabling apparmor for dhclient to have /usr linking to another partition sound smelly and unclean. I must be missing something. Things on Linux are clean.

I am sure that having /usr as symbolic link to a directory on another partition is not that uncommon and that it must be simple to achieve.

Any suggestions please? 

Thanks,
Deepesh

---

### Post by Ozymandias_117 on 2010-05-29
> **deepesh said:**
> Hi,
(sudo cp --preserve=all -r /usr /media/disk/usr_xyz) and just have symbolic link to it (/usr -> /usr/media/disk/usr_xyz).
I assume you mean "/usr -> /media/disk/usr_xyz"?

> I am sure that having /usr as symbolic link to a directory on another partition is not that uncommon and that it must be simple to achieve

I would say most people would just mount their partition to /usr rather than a symlink

---

### Post by deepesh on 2010-05-29
Thanks for your reply.

> **Ozymandias_117 said:**
> I assume you mean "/usr -> /media/disk/usr_xyz"?


Yes you are right. It should read /usr -> /media/disk/usr_xyz.

> **Ozymandias_117 said:**
> I would say most people would just mount their partition to /usr rather than a symlink

If I mount the whole partition on /usr, that partition cannot be used for any other purpose. Symbolic link allows for more flexibility.

---

### Post by amoun on 2010-05-30
Hi deepesh

I notice that there was no exact reply to your query, but I wonder have you thought of trying a mount. You could always make a small partition for user so the rest of the 80 gigs is accessible as you wish.

---

### Post by deepesh on 2010-06-02
> **amoun said:**
> Hi deepesh

I notice that there was no exact reply to your query, but I wonder have you thought of trying a mount. You could always make a small partition for user so the rest of the 80 gigs is accessible as you wish.

Thanks for your reply.

What I notice is that about 70% of storage consumed by installed application resides in /usr. I have three different [ku]buntu installations. If a separate /usr for each installation is created it will need six partitions. Keeping /usr linked to a directory in one of the large partitions keep number of partitions small and also makes more efficient use of storage. I know it's risky in case the large partition gets damaged or something, but that's a risk I am willing to take on my home computer to keep things simple.

Example in /etc/apparmor.d/tunables/alias specifically mentions aliasing /usr/ directory so I guess what I am trying to do is not uncommon and is something apparmor is designed to handle. I don't know why is it not working for me.

---

### Post by deepesh on 2010-06-13
> **deepesh said:**
> Thanks for your reply.

What I notice is that about 70% of storage consumed by installed application resides in /usr. I have three different [ku]buntu installations. If a separate /usr for each installation is created it will need six partitions. Keeping /usr linked to a directory in one of the large partitions keep number of partitions small and also makes more efficient use of storage. I know it's risky in case the large partition gets damaged or something, but that's a risk I am willing to take on my home computer to keep things simple.

Example in /etc/apparmor.d/tunables/alias specifically mentions aliasing /usr/ directory so I guess what I am trying to do is not uncommon and is something apparmor is designed to handle. I don't know why is it not working for me.

Disabled apparmor to get it working (not recommended).
[https://help.ubuntu.com/community/AppArmor#Disable](https://help.ubuntu.com/community/AppArmor#Disable) AppArmor framework

Simple steps for anyone looking for quick solution
For Ubuntu 9.10 (and later) using grub2:
1) Edit /etc/grub.d/40_custom (or can rename it to 08_custom if you like custom entries to appear before any other) and copy latest menuentry from 10_linux.
2) add apparmor=0 to kernel command line options.
It's the line which looks like
linux	/boot/vmlinuz-2.6.xx-xx..  root=UUID=xxxx...  apparmor=0
3) run update-grub to update /boot/grub/grub.cfg

---

### Post by Vegan on 2010-06-13
I found it was easier to just use a bigger disk and a single partition.

---

