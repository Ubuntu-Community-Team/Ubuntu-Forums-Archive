---
title: "LVM mirror creation problem"
date: 2012-07-22
forum: General Help
---

### Post by simonrodan on 2012-07-22
I am having problems creating a mirrored logical volume.

I have created two new physical volumes

```
root@ubuntu:/home/ubuntu# pvcreate /dev/sdc1 /dev/sdd1
  Physical volume "/dev/sdc1" successfully created
  Physical volume "/dev/sdd1" successfully created

```
I have created a volume group:
 ```

root@ubuntu:/home/ubuntu# vgcreate RAID1 /dev/sdc1 /dev/sdd1
  Volume group "RAID1" successfully created

root@ubuntu:/home/ubuntu# vgdisplay RAID1
  --- Volume group ---
  VG Name               RAID1
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  1
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               3.06 TiB
  PE Size               4.00 MiB
  Total PE              801288
  Alloc PE / Size       0 / 0   
  Free  PE / Size       801288 / 3.06 TiB
  VG UUID               ICsqOA-MMmL-wuOA-PqqA-oJ1o-vIeU-sG89xA

```

So far so good. I seem to have 3TB of free space to use.

I can create a striped volume

```
root@ubuntu:/home/ubuntu# lvcreate -i2 -l30%FREE -n test -I 128 RAID1
  Logical volume "test" created
root@ubuntu:/home/ubuntu# lvchange -an RAID1/test
root@ubuntu:/home/ubuntu# lvremove RAID1/test

```

However when I try to create a mirrored volume, I get this:

```
root@ubuntu:/home/ubuntu# lvcreate -n backup -m1 --mirrorlog mirrored -l 30%VG RAID1
  Not enough PVs with free space available for parallel allocation.
  Consider --alloc anywhere if desperate.
  Unable to allocate extents for mirror(s).

```

Very puzzling. Can anyone tell me what I'm doign wrong?

Many thanks

---

### Post by simonrodan on 2012-07-22
Problem solved - user error. I didn't give the vg 2 additional volumes needed for the disk log.

---

### Post by Nakarti on 2013-01-28
I would argue this is a defaults 'bug' in lvm: Logically (and this is the case in every other LVM mirroring I have used, AIX and HP-UX JFS2, VeritasVM, SolarisVM, ZFS,) if you are mirroring the log, it is safe and should be assumed that the logs will be on the same volume as the data.
That is what adding '--alloc anywhere' does, and I use it for all my mirrors.
Even with a dodgy drive (it's actually a dodgy cable, been haunting me for several drives but with the mirror the OS doesn't hang,) it recovers the mirror headless and alone after a reboot with mirrored local mirrorlog.

If you are going to put the log on a third device, it can be a single drive. It just devolves to corelog if the mirrorlog disk fails.

---

