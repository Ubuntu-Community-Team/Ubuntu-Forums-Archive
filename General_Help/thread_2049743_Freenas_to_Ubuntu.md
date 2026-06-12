---
title: "Freenas to Ubuntu"
date: 2012-08-29
forum: General Help
---

### Post by grammasta on 2012-08-29
So I have a freenas setup on my nas, but I want to install Ubuntu...mostly because of Plex. Currently I have 5x 2TB drives formatted as ufs, 1 is almost empty, so I wanna format this to ext4(that's what I should run in linux right?) and use that to copy stuff over. Is this the easiest way to do it? Copy one hdd at the time over to the ext4 formatted one, then format the hdd i copied from to ext4 and then copy back?

But ufs should be readable in Ubuntu right?

---

### Post by CrusaderAD on 2012-08-29
> **grammasta said:**
> Copy one hdd at the time over to the ext4 formatted one, then format the hdd i copied from to ext4 and then copy back?

That's probably the easiest way to do it. You can use gparted to manage the formatting, just be careful!

---

### Post by grammasta on 2012-08-29
So reading the ufs drives in Ubuntu shouldn't be a problem? It's just writing to them that doesn't work? Maybe save a list of what drives are mounted as what before I start formatting?

And ext4 is the way to go? (lots of questions! :))

---

### Post by CrusaderAD on 2012-08-29
ext4 will work fine. ufs shouldn't be a problem. Check [this]("http://askubuntu.com/questions/85154/mount-ufs-filesystem") out.

---

### Post by grammasta on 2012-08-29
Thanks. I'll try that after the install. Should the disks be added in Ubuntu? So it's just the mounting I have to do?

---

### Post by CrusaderAD on 2012-08-29
I think gparted requires the disk to be unmounted in order to make changes, but if you're in Ubuntu, it will detect whatever is connected at the time. It's a pretty easy program to use. You'll get the hang of it real quick.

---

### Post by Lars Noodén on 2012-08-29
UFS should be readable in Ubuntu, but I think it isn't.  When I try to mount a FFS (UFS) formatted drive in 12.10 I get the following error:

```

[ 5256.989888] sd 2:0:0:0: [sdb] No Caching mode page present
[ 5256.995617] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 5257.001249] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 5270.890871] ufs was compiled with read-only support, can't be mounted as read-write
[ 5373.727274] ufs was compiled with read-only support, can't be mounted as read-write

```

The work-around is to mount it read-only, but that is of very limited value.  And even then it appears that I can't read the disk and I get an Input/output error.  So, although in theory there is UFS support in Ubuntu, I would say that in practice there probably isn't. 

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/181452](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/181452)

About your 5 drives.  You could set 4 or 5 of them up as a RAID 5 or RAID 6 array using [mdadm](http://manpages.ubuntu.com/manpages/precise/en/man8/mdadm.8.html).

---

### Post by grammasta on 2012-08-29
> **Lars Noodén said:**
> UFS should be readable in Ubuntu, but I think it isn't.  When I try to mount a FFS (UFS) formatted drive in 12.10 I get the following error:

```

[ 5256.989888] sd 2:0:0:0: [sdb] No Caching mode page present
[ 5256.995617] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 5257.001249] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 5270.890871] ufs was compiled with read-only support, can't be mounted as read-write
[ 5373.727274] ufs was compiled with read-only support, can't be mounted as read-write

```

The work-around is to mount it read-only, but that is of very limited value.  And even then it appears that I can't read the disk and I get an Input/output error.  So, although in theory there is UFS support in Ubuntu, I would say that in practice there probably isn't. 

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/181452](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/181452)

About your 5 drives.  You could set 4 or 5 of them up as a RAID 5 or RAID 6 array using [mdadm](http://manpages.ubuntu.com/manpages/precise/en/man8/mdadm.8.html).

What's the benefit of doing that over single drives?

---

### Post by Lars Noodén on 2012-08-29
> **grammasta said:**
> What's the benefit of doing that over single drives?

The main advantage with RAID is that if a drive fails, you will not lose any data.  It's not a substitute for backup, but prevents against device failure.  When one fails in a RAID array, it would just be a matter of replacing the dead drive and having the array repair itself.  Another advantage is that they array appears as a single drive rather than a bunch of smaller ones.  The different RAID levels have varying performance, efficiency and robustness.  RAID Level 5 or 6 might be useful to look at.  There's a *lot* written on the net about RAID.

---

