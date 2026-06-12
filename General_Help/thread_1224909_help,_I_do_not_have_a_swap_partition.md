---
title: "help, I do not have a swap partition"
date: 2009-07-27
forum: General Help
---

### Post by dannybuntu on 2009-07-27
I installed Ubuntu 9.04 and allocated a swap partition.

Then I installed Debian

Then when I logged into Ubuntu I noticed that my swap is 0/0 in htop.

I checked sysinfo and sure enough Ubuntu does not have a swap partition!

Any ideas?

---

### Post by philcamlin on 2009-07-27
you installed debian in the seap partition :O

you can make one in gparted by partitioning

---

### Post by dannybuntu on 2009-07-27
> **philcamlin said:**
> you installed debian in the seap partition :O

you can make one in gparted by partitioning

No, its still there. It looks like it's not mounted. Quite odd.

---

### Post by bodhi.zazen on 2009-07-27
Ubuntu mounts partitions by UUID

I am guessing Debian re-formated the swap and the UUID changed.

You can check this with

```
sudo blkid
```

And 

```
grep swap /etc/fstab
```

Simply update your /etc/fstab with the corect UUID

```
gksu gedit /etc/fstab
```

---

### Post by SunnyRabbiera on 2009-07-27
Well depending on how much ram you have Swap might not be needed.
How much ram do you have?

---

### Post by dannybuntu on 2009-07-27
> **bodhi.zazen said:**
> Ubuntu mounts partitions by UUID

I am guessing Debian re-formated the swap and the UUID changed.

You can check this with

```
sudo blkid
```

Result:

/dev/sda1: UUID="2d85ee2b-2944-4e91-aff4-4744c389de26" TYPE="ext3"
/dev/sda5: TYPE="swap"
/dev/sda6: UUID="c0f699cf-5cb9-44a7-9c81-90ead670719c" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="1A4492104491EF2F" LABEL="databack" TYPE="ntfs"
/dev/sdb2: LABEL="UNIVBACK" UUID="488F-478E" TYPE="vfat"
/dev/sdc1: UUID="4497efb0-94bd-46bf-a82b-a7d3c278e5fa" SEC_TYPE="ext2" TYPE="ext3"
> 
```
grep swap /etc/fstab
```

Result:
# swap was on /dev/sda5 during installation
UUID=3368a010-45cd-4b03-9af9-206508ef1c18 none            swap    sw  0       0

> Simply update your /etc/fstab with the corect UUID

```
gksu gedit /etc/fstab
```

The correct UUID is 3368a010-45cd-4b03-9af9-206508ef1c18 right?

> How much ram do you have?

717 MB

some are shared

---

### Post by bodhi.zazen on 2009-07-28
It does not appear debian gave your swap a UUID.

You can change the entire "UUID=xxx.yyy.xzzz" to

```
/dev/sda5 none            swap    sw  0       0
```

Save your changes

Then :

```
sudo swapon -a
free -m
```

And we should see your swap

---

