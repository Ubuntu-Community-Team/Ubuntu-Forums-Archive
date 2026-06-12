---
title: "Recreating mdadm array in 10.04 after upgrade from 9.04?"
date: 2010-07-31
forum: General Help
---

### Post by GCT on 2010-07-31
I had a raid array working great in 9.04 with mdadm, and I just recently upgraded to 10.04 (clean install) and I'm trying to reassemble the array and having a dickens of a time.

When I try to recreate the array with:

```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdd /dev/sdc

```

I get this:

```
mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: Cannot open /dev/sdd: Device or resource busy
mdadm: Cannot open /dev/sdc: Device or resource busy
mdadm: create aborted

```

But I don't see the drives in use anywhere (checking mount, dmesg, fuser, etc).  Running mdadm -E on each drive says it can't find a superblock on them either.  Can anyone help me figure this out?

Note - I do see this in my dmesg:

```

[    4.000065] device-mapper: dm-raid45: /dev/sdb is raid disk 0
[    4.000068] device-mapper: dm-raid45: /dev/sdd is raid disk 1
[    4.000070] device-mapper: dm-raid45: /dev/sdc is raid disk 2

```

Perhaps dmraid is getting in my way?

---

### Post by GCT on 2010-07-31
After a little bit of searching I was able to add "nodmraid" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub to disable the dmraid drivers on boot. 

After doing this my mdadm --create worked just fine, and the array is rebuilding right now.  Still trying to get it to mount though.

---

### Post by prodigy_ on 2010-07-31
I hope you are aware that **--create** will create a new array rather than reassembling your old one.

---

### Post by GCT on 2010-07-31
Does --create actually write anything to the array though or will it assemble the array from the given drives?

---

### Post by jacekk015 on 2010-07-31
Like the name says it creates new array.
There is no assurance that it will be assembled instead.

I'm thinking that if the array is rebuilding that you're in a bad situation.

---

### Post by GCT on 2010-07-31
Damn, mdadm even says it's supposed to warn you if you try to create using disks that already have raid superblocks.  Do you think there's anything I can do to get it working again?  Rewrite the partition table with gpart maybe?

---

### Post by GCT on 2010-07-31
Anyone know how I can fix this or am I hosed?

---

### Post by prodigy_ on 2010-07-31
If your array was ok and mdadm didn't give you any warnings, maybe everything will be alright. Sometimes mdadm is actually quite smart. Still, I wouldn't use anything than **--assemble** or **--assemble --scan** on an existing array.

---

### Post by GCT on 2010-07-31
Yeah I don't know, it's not wanting to mount now though.

---

### Post by jacekk015 on 2010-08-01
Give us:
```
sudo sfdisk -l -uS /dev/md0
```

It will show you partitions on RAID md0.

---

