---
title: "where'd my space go? o.O"
date: 2009-12-22
forum: General Help
---

### Post by Th3Professor on 2009-12-22
My root partition is 19G size, 15G used, 3.3G avail.
My /home is part of / and is using 8.4G.
Running Ubuntu Studio 8.10, surely the system alone isn't taking up 10.4G? Or 6.6G? Any ideas on how to track down exactly where the space is being used? I'm trying to move files over to another hard drive before putting Ubustu 9.10 on.

---

### Post by synapsys on 2009-12-22
Try

```
df -h
```in terminal

6.6Gb sounds about right for /

---

### Post by Th3Professor on 2009-12-22
> **synapsys said:**
> Try

```
df -h
```in terminal

6.6Gb sounds about right for /

did that but not sure what's up w/ things still...
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G   15G  3.3G  82% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  120K  2.0G   1% /var/run
varlock               2.0G  4.0K  2.0G   1% /var/lock
udev                  2.0G  2.9M  2.0G   1% /dev
tmpfs                 2.0G  1.7M  2.0G   1% /dev/shm
lrm                   2.0G  2.4M  2.0G   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda1             942M   72M  823M   9% /boot
/dev/sda6             216G  201G  4.2G  98% /studio/workspace
/dev/sda2             187G  107G   80G  58% /windows
/dev/mapper/vg0-vault
                      755G  258G  498G  35% /studio/vault
/dev/mapper/vg0-zone   87G  184M   83G   1% /zone
/dev/mapper/vg0-nomad
                       87G  342M   82G   1% /nomad
/dev/sdi1             932G  765G  167G  83% /media/My Book
/home/x/.Private    19G   15G  3.3G  82% /home/x/Private
/dev/scd0             1.5G  1.5G     0 100% /media/cdrom0

```6.6+8.4= 15... it's a 19G partition. :-/
The 'private' partition thing within / is only taking 6.2M, so it's not that. :(

It the OS is taking 6.6 gigs, then where's that approximate 4 gigs going?

...wait... could it be SWAP?

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         122      979933+  83  Linux
/dev/sda2   *         123       24437   195310237+   7  HPFS/NTFS
/dev/sda3           24438       26261    14651280   be  Solaris boot
/dev/sda4           26262       60801   277442550    5  Extended
/dev/sda5           26262       28693    19535008+  83  Linux
/dev/sda6           28694       57263   229488493+  83  Linux
/dev/sda7           57264       57506     1951866   82  Linux swap / Solaris
/dev/sda8           57507       57749     1951866   82  Linux swap / Solaris
/dev/sda9           57750       57992     1951866   bf  Solaris
/dev/sda10          57993       60801    22563261   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c177d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000caa62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d3415

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001    c  W95 FAT32 (LBA)

```...no... swap = other partition(s)

so far the biggest space hoggers i can find outside of /home within the / partition are:
/lib (477M)
/usr (4.5G)
/var (661M)

I can see the 4G disappearing *if* it is going into /usr ...but isn't /usr part of the actual operating system? (part of the main install?)

---

### Post by Th3Professor on 2009-12-22
Is /usr part of the main operating system install?

---

### Post by dcstar on 2009-12-22
> **Th3Professor said:**
> My root partition is 19G size, 15G used, 3.3G avail.
My /home is part of / and is using 8.4G.
Running Ubuntu Studio 8.10, surely the system alone isn't taking up 10.4G? Or 6.6G? **Any ideas on how to track down exactly where the space is being used**? I'm trying to move files over to another hard drive before putting Ubustu 9.10 on.

```
gksudo baobab
```

---

### Post by Th3Professor on 2009-12-22
Awesome thank you!

Do you by chance know if I need to stop my raid on my extra hard drives before installing a new OS on the main (separate) hard drive?

---

### Post by dcstar on 2009-12-22
> **Th3Professor said:**
> Awesome thank you!

Do you by chance know if I need to stop my raid on my extra hard drives before installing a new OS on the main (separate) hard drive?

As long as you are not using the RAID for install you probably don't need to.

---

### Post by Th3Professor on 2009-12-22
I'm using LVM too, do you know if i need to make any preparations for that prior to a fresh OS install?

edit-
I'll be backing up crucial data first of course but with multiple terabytes of data there is no way i'm gonna back all of that up. lol just high priority things. otherwise, i'm not really sure what needs to be done w/ raid (raid5 via mdadm) and/or lvm (linux volume management) prior to installing the new OS.

---

