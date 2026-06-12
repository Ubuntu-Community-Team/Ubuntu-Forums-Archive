---
title: "GParted Question"
date: 2010-04-30
forum: General Help
---

### Post by barnaclebill18 on 2010-04-30
Hello,

I am trying to get my hard drive ready for 10.04, here is the problem I am having.

I want to expand sda5 and use that unallocated 19.04 GiB to put 10.04 on.

9.10 is on sda4, and I would like to keep it as is.

When I try to resize sda5, the only option is to make it smaller.

If I try to resize sda4, I have the option to make it larger or smaller.

Thanks.

---

### Post by BeRA on 2010-04-30
I had a similar situation a couple of years ago... as far as I know: you cannot expand a partition to include unallocated space thats placed before that partition... this is what I would do if I was in your place: Backup content of sda5 to sda4 (in some new folder... it looks like you have enough free space for that), then erase sda5, and create a new partition that will include that unallocated 19.04GB + free space that you got by erasing "old" sda5... install 10.04 on that new partition and than copy back that data you backup-ed on sda4... erase backup you made on sda4...

I don't know what you have on that sda5 at the moment, but if you can backup that and if I understood what you want... than this might do the trick...

Maybe there is some other way, but this is what I would do...

---

### Post by psusi on 2010-04-30
sda5 and sda6 are both logical partitions contained within the extended partition.  sda6 is in use, so neither it nor the extended partition it contains can be manipulated, which is why the little locked/key icons show up.  Unmount your swap partition and you should be able to expand the extended partition to consume the free space.

Oh, and does sda5 have data on it?  It shouldn't if you are going to install lucid there.  If so, delete it and recreate it after you have expanded the extended partition, rather than resize it since that will take a long time.

---

### Post by srs5694 on 2010-04-30
> **BeRA said:**
> I had a similar situation a couple of years ago... as far as I know: you cannot expand a partition to include unallocated space thats placed before that partition...

This is untrue.

The two main issues that barnaclebill18 faces are that he's trying to modify in-use partitions and he must first expand the extended partition that encloses /dev/sda5 before he can resize /dev/sda5. In order, then:

To do anything with the disk, barnaclebill18 must boot using an emergency disc of some sort, such as [PartedMagic](http://partedmagic.com/) or [System Rescue CD.](http://www.sysresccd.org/) Once booted, it may be necessary to disable swap space. (Anything marked in GParted by the keys is currently in use and therefore locked. You can usually stop using a partition by right-clicking it and selecting "Unmount" or a similar option, but this isn't possible if the system has booted from the partition.) Extended partitions should become unused once all the logical partitions they contain are unmounted or swap space disabled.

Once nothing is in use, it should be possible to select the extended partition (/dev/sda2) and resize it to the left, effectively moving the unallocated space into the extended partition. It should then be possible to select /dev/sda5 and resize/move it. Moving a partition or resizing it to the left, though, is likely to be time-consuming, and it's riskier than resizing the right side of the partition. Backing up before such an operation is advisable.

---

### Post by barnaclebill18 on 2010-04-30
srs5694,

The screen shot shown was taken using the installed GParted, but I used a live GParted disc when trying to change the partition size.

I also thought I could enlarge sda5, it has 9.04 on it and I will save my Home files before I delete it, I wanted to make it larger before installing 10.04 and was just looking with GParted, but the option is not there.

---

### Post by barnaclebill18 on 2010-04-30
> **BeRA said:**
> I had a similar situation a couple of years ago... as far as I know: you cannot expand a partition to include unallocated space thats placed before that partition... this is what I would do if I was in your place: Backup content of sda5 to sda4 (in some new folder... it looks like you have enough free space for that), then erase sda5, and create a new partition that will include that unallocated 19.04GB + free space that you got by erasing "old" sda5... install 10.04 on that new partition and than copy back that data you backup-ed on sda4... erase backup you made on sda4...

I don't know what you have on that sda5 at the moment, but if you can backup that and if I understood what you want... than this might do the trick...

Maybe there is some other way, but this is what I would do...

This sounds like the way  I should go, thanks.

---

### Post by BeRA on 2010-04-30
> **barnaclebill18 said:**
> This sounds like the way  I should go, thanks.

You're welcome :)


PS. I wasn't right what I said that "you cannot expand a partition to include unallocated space thats placed before that partition" so that's why I wrote "as far as I know" to let you know I was not sure about that statement... both psusi and srs5694 are right and I've learned something new myself (to both of them: thanks for correcting me :) )... 

finally, I'm happy that you found my proposal (that will work just as fine as the other) to be the easiest one. :)

---

### Post by srs5694 on 2010-04-30
> **barnaclebill18 said:**
> I also thought I could enlarge sda5, it has 9.04 on it and I will save my Home files before I delete it, I wanted to make it larger before installing 10.04 and was just looking with GParted, but the option is not there.

As I said, you've got to enlarge your extended partition (/dev/sda2) *before* you enlarge /dev/sda5. Until you enlarge /dev/sda2, there will be no room to enlarge /dev/sda5, since /dev/sda5 must reside entirely within the confines of /dev/sda2.

Even if you delete /dev/sda5 and then re-create it with a larger size (which will certainly work), you'll need to either shrink or enlarge /dev/sda2 before you create the new partition, since when you delete /dev/sda5, you'll end up with two bocks of free space, one inside and one outside of the extended partition. No partition may span that boundary, so you'll have to change it in order to create a single partition that uses all that free space. (OTOH, some partitioning tools may change the extended partition automatically, so you might not need to do this explicitly -- but it'll still be done behind the scenes.)

As you may be gathering by now, extended partitions are a pain in the tush! :rolleyes:
They're one of the reasons I now use the GUID Partition Table (GPT) scheme whenever possible, since it does away with the primary/extended/logical partition distinctions -- but in it infinite wisdom, Microsoft has decreed that Windows won't boot from GPT disks on BIOS-based computers. :rolleyes::rolleyes::rolleyes: (Linux, FreeBSD, and some other OSes have no problems with this.)

---

### Post by barnaclebill18 on 2010-04-30
> **srs5694 said:**
> As I said, you've got to enlarge your extended partition (/dev/sda2) *before* you enlarge /dev/sda5. Until you enlarge /dev/sda2, there will be no room to enlarge /dev/sda5, since /dev/sda5 must reside entirely within the confines of /dev/sda2.

Even if you delete /dev/sda5 and then re-create it with a larger size (which will certainly work), you'll need to either shrink or enlarge /dev/sda2 before you create the new partition, since when you delete /dev/sda5, you'll end up with two bocks of free space, one inside and one outside of the extended partition. No partition may span that boundary, so you'll have to change it in order to create a single partition that uses all that free space. (OTOH, some partitioning tools may change the extended partition automatically, so you might not need to do this explicitly -- but it'll still be done behind the scenes.)

As you may be gathering by now, extended partitions are a pain in the tush! :rolleyes:
They're one of the reasons I now use the GUID Partition Table (GPT) scheme whenever possible, since it does away with the primary/extended/logical partition distinctions -- but in it infinite wisdom, Microsoft has decreed that Windows won't boot from GPT disks on BIOS-based computers. :rolleyes::rolleyes::rolleyes: (Linux, FreeBSD, and some other OSes have no problems with this.)

You are right, I forgot about the extended partition.

This is what it looks like now. I probably should have deleted it first, because it took a long time to apply the changes.

Thanks to all, I will mark thread solved.

---

