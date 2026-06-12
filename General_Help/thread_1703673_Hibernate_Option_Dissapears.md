---
title: "Hibernate Option Dissapears"
date: 2011-03-09
forum: General Help
---

### Post by fleamour on 2011-03-09
I increasingly use Ubuntu so swapped SATA ports 1&2 around so now 7 boots from BIOS F11 pop out menu.

Windows did not complain so far but hibernate is missing from Ubuntu's power down options.  I installed Ubuntu Tweak, but cannot see an option to re-enable.  

Is this something to do with the swapped HDDs &/or the swap partition?  Or more likely a recent update?

---

### Post by fleamour on 2011-03-09
I think maybe I have no swap as of now. 

cat /etc/fstab returns:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=7c6f7176-45f9-4df0-897b-00f4075661b4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb4 during installation
UUID=9e598d1e-ce06-4c5a-b634-9814f7a01a18 /home           ext4    defaults        0       2
/dev/sdb5       none            swap    sw              0       0

```

But returns this error:

```
user@computer:~$ sudo swapoff -a
[sudo] password for user: 
user@computer:~$ sudo /sbin/mkswap /dev/sbd5
/dev/sbd5: No such file or directory
```

Also:

```
swapon: /dev/sdb5: stat failed: No such file or directory
```

---

### Post by fleamour on 2011-03-09
OK, here's the rub:

```
sudo fdisk -l
```

Returns swap as dev/sda5, which is now correct.

However:

```
cat /etc/fstab
```

Returns swap as dev/sdb, which it was before.  Ubuntu is confused, how can I rectify?

---

### Post by fleamour on 2011-03-09
Ahhh, (dawns.)  It all falls into place.  Only when my thoughts are concrete can I make sense of what I initially thought to be a complex problem.

So...


```
sudo gedit /etc/fstab
```

Edit dev/sd***b***5 to dev/sd***a***5

Then:

```
sudo swapoff -a
sudo /sbin/mkswap /dev/sda5
sudo swapon -a
```

& I'm assuming after a reboot hibernate will be good to go, not that I ever use it!

EDIT: YEY!

---

