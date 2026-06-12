---
title: "'df' numbers don't add up.  Missing space!"
date: 2009-09-20
forum: General Help
---

### Post by Huufarted on 2009-09-20
below is the output of 'df'.  My understanding is this:

Avail + Used = Size.  is this not the case?  Please look at /dev/sda7.  It shows 868G total, 823G used, that should leave approx 45G free, correct?

```
art@atom1:/var/log/fsck$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              46G  7.0G   37G  16% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  352K 1007M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.7M 1005M   1% /dev
tmpfs                1008M     0 1008M   0% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda7             868G  823G 1017M 100% /home
art@atom1:/var/log/fsck$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             48062376   7247912  38372992  16% /
tmpfs                  1031472         0   1031472   0% /lib/init/rw
varrun                 1031472       352   1031120   1% /var/run
varlock                1031472         0   1031472   0% /var/lock
udev                   1031472      2700   1028772   1% /dev
tmpfs                  1031472         0   1031472   0% /dev/shm
lrm                    1031472      2004   1029468   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda7            909519472 862277976   1040568 100% /home
art@atom1:/var/log/fsck$

```

---

### Post by Mister.Vash on 2009-09-20
It's probably the space reserved for root, which I think defaults to 5% of the volume.  Since that is your home folder, you probably don't need that.

run the following command to list what it is:
```

sudo tune2fs -l /dev/sda7

```

Look at the output for "Reserved block count"  that multiplied by the block size will show you how much space your normal account can't use.

The man page for tune2fs describes how to change the reserved blocks, or you could take a quick look on the forum for examples of using tune2fs.

---

### Post by mcduck on 2009-09-20
5% of disk space on Ext filesystems is reserved for root user only, and therefore doesn't count as being available for any other user. This is to prevent normal users from filling the drive to the point that would make the system unable to boot any more.

Since /dev/sda7 is not your root partition you could safely reduce the amount of reserved space on that filesystem, this can be done with the tune2fs command.

---

### Post by Huufarted on 2009-09-20
Can it safely be reduced to 0, effectively freeing the entire partition to be used by normal users?

---

### Post by mcduck on 2009-09-21
> **Huufarted said:**
> Can it safely be reduced to 0, effectively freeing the entire partition to be used by normal users?

Yes, if the partition is not your root partition you can safely set the reserved space to 0.

For rot partition you should always have some space reserved for root, but these days the disks are so big that 5% is often way more than what's needed. I'd say keeping a gigabyte or two reserved for root should be enough.

Although one thing to consider is that while disk fragmentation isn't usually much of a problem with Linux file systems, it will increase when the disk starts running out of space and if you get close to 100% disk usage you will definitely get lots of fragmentation and the disk will become slow. So you really don't want to fill your drives to 100% anyway..

---

### Post by wdaniels on 2010-06-20
> **mcduck said:**
> 5% of disk space on Ext filesystems is reserved for root user only, and therefore doesn't count as being available for any other user. This is to prevent normal users from filling the drive to the point that would make the system unable to boot any more.

Since /dev/sda7 is not your root partition you could safely reduce the amount of reserved space on that filesystem, this can be done with the tune2fs command.

Wow, I didn't know this!

That little trick just got me 100G for free on a stupidly huge (1.8T) root partition I was working with :D Seems a bit daft to use a percentage - not like root is really going to *need* 100G to boot/repair a system ever.

While I would never create one huge root partition like that myself, it seems that many automated installers operated by inexperienced (i.e. Windows) admins end up doing this. I see it very often.

Anyway, thanks!

---

