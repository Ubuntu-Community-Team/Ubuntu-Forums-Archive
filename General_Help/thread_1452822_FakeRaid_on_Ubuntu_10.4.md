---
title: "FakeRaid on Ubuntu 10.4"
date: 2010-04-12
forum: General Help
---

### Post by daz4126 on 2010-04-12
Hi,

I'm trying to install beta 2 on a new system that has FakeRaid and want to get Raid 1 working.

I am following the guide for Karmic here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I get the following output from the terminal, which seems to suggest it is working:

```
sudo dmraid -r
/dev/sdb: nvidia, "nvidia_ecdhabfd", mirror, ok, 488397166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_ecdhabfd", mirror, ok, 488397166 sectors, data@ 0
```

But the first problem I run into is that Gparted doesn't recognise the 'fake' mirror drive (nvidia_ecdhabfd), it just shows the two drives separately as sda and sdb.

Can anybody help with this? Is there a way to create the required partitions before launching the installer?

cheers,

DAZ

---

### Post by prodigy_ on 2010-04-12
Try to install from Alternate CD.

---

### Post by daz4126 on 2010-04-12
Hi prodigy,

Thanks for the advice. I've just tried the alternate CD and it does detect that RAID is present and only shows the one drive. Unfortunately when I choose "Write Changes to disks", I immediately get the following error message on a Red Screen of Death:
```
The ext4 file system creation in partition #1 of Serial ATA RAID nvidia_aiddadgb (mirror) failed.
```

I don't know why this is - seems that the disks can't be accessed for some reason.

Any ideas anybody??

cheers,

DAZ

---

### Post by daz4126 on 2010-04-12
I didn't realise RAID was going to be such a big pita - is it worth just disabling RAID and using the two drives separately with the second one as a backup drive?

cheers,

DAZ

---

### Post by prodigy_ on 2010-04-12
Well, you don't have to use fakeRAID. In fact, I'd even advise against that because such solutions aren't known for their reliability.

Instead, you could make software RAID1 during the installation. Read [this HOWTO](https://help.ubuntu.com/community/Installation/SoftwareRAID).

---

### Post by daz4126 on 2010-04-12
Ye, I'm beginning to see that fakeRAID is a bit pants. What exactly is software RAID? Do you think this would be better than just using the second HD as a backup drive (either manually or using something like rsync)?

thanks for the help,

DAZ

---

### Post by prodigy_ on 2010-04-12
Software RAID is a RAID implemented entirely by the means of the OS. Linux uses mdadm utility for that.

Pros:
- you don't have to rely on that (usually ultra-cheap) integrated MB-integrated RAID controller;
- if your MB will die, you still can continue to use the RAID with different hardware;
- you can move the RAID to another PC w/o reassembling it from scratch.

Cons:
- it uses more system resources (but not by a substantial margin);
- mdadm isn't a very user-friendly tool.

Separate disks with scheduled backup (during nighttime, for example) is an OK solution too. So the choice is up to you.

---

### Post by daz4126 on 2010-04-12
Thanks prodigy, you've been really helpful. I'm going to turn the fakeRAID off in the Bios and install. Just one last question - can I set up software RAID after install or do I have to do it when I install?

Thanks again,

DAZ

---

### Post by prodigy_ on 2010-04-12
> **daz4126 said:**
> can I set up software RAID after install

Sure, if you have a spare drive for your installation and want only your data to be stored on RAID.

In any case, whenever you create a RAID0 or RAID5, all member drives are completely erased. I'm not sure if that's true for mirroring (RAID1) however. Maybe someone else can answer.

---

### Post by daz4126 on 2010-04-13
Thanks a lot for all your help prodigy_

I'm going to just install it to one disk and then wait and see before deciding what to do with the second disk.

cheers,

DAZ

---

### Post by rollyar on 2010-05-17
I have this problem too.

ubuntu has no  support fakeraid for these nvidia devices????
excuse  my ignorance, I am an inexperienced user.

-there  is a alternate solution to this allowing use fakeraid in ubuntu not software?
-there  is a distribution that does?

thanks,  sorry for my bad english.

---

### Post by bjnhg on 2010-05-19
Hi all,

I'v experienced those problems recently.

I've tried the Alternate CD and get exaclty the same problem as stated before on filesystem creation. 
I'm using RAID1 on ICH9R. The devices created ( by udev ?? ) on installation are :
/dev/mapper/isw_*******
/dev/mapper/isw_*******1
/dev/mapper/isw_*******2
/dev/mapper/isw_*******3


It seems that the partitioner is expecting instead
/dev/mapper/isw_******p1
/dev/mapper/isw_******p2
...

That's the first problem. If you succed this step, you'll need to pass the GRUB2 problem.

I've solved this problem by installaling my system on another JBOD disk ( GRUB MBR + "/boot" + "/" - LVM )
_ After booting in this fresh install, I've moved the "/" volume on the RAID device using LVM :
pvcreate / vgextend / pvmove / vgreduce / pvdelete
_ Then I've dumped/restored the /boot filesystem from JBOD to RAID1.
_ I've recreate the grub2 environment : grub-install /dev/mapper/isw_*******
_ and lately grub-mkconfig.

It seems to work correctly, but you need to have a free disk in your system.

cheers,

---

### Post by daz4126 on 2010-05-21
I just gave up in the end and am using Back In Time to back up to the second hard drive. It just seems easier than jumping through all those hoops.

DAZ

---

### Post by pdk on 2010-05-27
Turn off the fakeraid and use the disks normally. Create the raid during the install.

---

