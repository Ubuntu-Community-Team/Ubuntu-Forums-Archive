---
title: "Change I/O scheduler using UUID to refer to the disk"
date: 2011-09-02
forum: General Help
---

### Post by Prodoc on 2011-09-02
Hi,

I'd like to change the I/O scheduler to deadline for one particular disk on my system. All resources I found, however, use methods I can not use because they either refer to the disk using labels (sda, sdb, etc.) or they are using Grub instead of Grub2.

The reason I can't use labels to refer to a disk is obvious, it can and will change for a disk. How does one change the I/O scheduler using a UUID to refer to the disk?

Any of the following are no option:

In */etc/default/grub*
```
GRUB_CMDLINE_LINUX_DEFAULT="elevator=deadline quiet splash"
```
Would cause the same scheduler to be used for all disks.

In */etc/rc.local*
```
echo deadline > /sys/block/sda/queue/scheduler
echo 1 > /sys/block/sda/queue/iosched/fifo_batch
```
Is using the labels.

In */etc/sysfs.conf*
```
block/sda/queue/scheduler = deadline
```
Is using the labels again.

---

### Post by Prodoc on 2011-09-03
Does the lack of a reply mean it is not possible to achieve it using a UUID? Is there a different way to make sure the scheduler is changed for the correct drive without having to do it manually after each boot?

---

### Post by Prodoc on 2011-09-05
FYI: I ended up creating my own init.d script: [http://stackoverflow.com/questions/7294719/change-i-o-scheduler-not-using-sd-to-refer-to-the-disk](http://stackoverflow.com/questions/7294719/change-i-o-scheduler-not-using-sd-to-refer-to-the-disk)

---

### Post by Singtoh on 2012-02-20
> **Prodoc said:**
> FYI: I ended up creating my own init.d script: [http://stackoverflow.com/questions/7294719/change-i-o-scheduler-not-using-sd-to-refer-to-the-disk](http://stackoverflow.com/questions/7294719/change-i-o-scheduler-not-using-sd-to-refer-to-the-disk)

You could try this as I have done, it seems to work nicely. I am using a SSD with a HDD in the same machine. [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Its about half way down the page and it uses /etc/rc.local to use the SSD's device ID to determine its /dev/ node to set whatever scheduler you like. Here is the code anyway: 

SSD=(ata-OCZ-ONYX_XA1Y7CE3709UG79OTHVM ata-SAMSUNG_SSD_830_Series_S0VTNYABA01063)

declare -i i=0
while [ "${SSD[$i]}" != "" ]; do
  NODE=`ls -l /dev/disk/by-id/${SSD[$i]} | awk '{ print $NF }' | sed -e 's/[/\.]//g'`
  echo noop > /sys/block/$NODE/queue/scheduler
  i=i+1
done

But go give it a read anyway, its very informative.

Cheers,

Singoth

---

### Post by kohtala on 2012-07-11
A bit late, I found this while looking if anyone had any "official" fix for this kind of things, but FYI something that could be another solution to this.

Actually you want to change the scheduling for the disk that has a partition with filesystem with specific UUID? You can match the partition in udev and fortunately the disk is always the parent.

Therefore a file with one line should be enough, substituting xx for your filesystem UUID:

/etc/udev/rules.d/95-uuid-ioscheduler.rules:
```
ENV{ID_FS_UUID}=="xx", ATTR{../queue/scheduler}="deadline"
```

---

