---
title: "RAID + LVM install on an Acer Altus G320 Server"
date: 2006-05-24
forum: General Help
---

### Post by pedrocr on 2006-05-24
I tried to install ubuntu 5.10 on an Acer Altus G320 using RAID and LVM. It has two 250GB SATA disks. I used the regular install CD in "server" mode.

I partitioned it by first creating a RAID1 array between the two drives and then creating swap/var/usr/home/root partitions using LVM. The first part of the installation went fine and installed lilo on /dev/md0.

When I rebooted to finish the installation the machine didn't boot asking for a boot device. Apparently no LILO was found.

I've done the same install on a different machine and it worked. Anyone have any idea why LILO isn't being found/correctly installed?

---

### Post by astrocrep on 2006-05-24
The /boot needs to be on the raid 1 array as well... plus I think lilo needs to be below 1gb or something...

Why not use Grub.

My Raid array is:
md0 (raid1)(ext3) /boot
md1 (raid0)(rfs) /

-Rich

---

### Post by pedrocr on 2006-05-24
I didn't use Grub because the installer defaults to LILO for these cases. This same instalation procedure has worked in another machine although that one only has 80 GB disks. Maybe it's the size of the disk?

I didn't use a /boot partition.

---

### Post by pedrocr on 2006-05-24
I tried creating two md devices. One in the first 200MB for the /boot and the other with the rest for the lvm physical volume. This made the installer default to grub but it still didn't boot afterwards. I'm out of ideas of what it might be. Anyone?

---

### Post by pedrocr on 2006-05-25
Anyone have any suggestion on this? I'm stuck. During the instalation I get some warnings that linux wasn't informed of the changes to the partition table of the md device but I think I've read somewhere those are bogus. Anyone have any idea of what the problem might be?

---

### Post by pedrocr on 2006-06-02
Just for the record I solved this by creating two raid devices. md0 has /boot on it and md1 has the other partitions (including swap) in LVM. I then had to mark the two partitions that compose md0 as bootable. Grub was installed and works.

---

