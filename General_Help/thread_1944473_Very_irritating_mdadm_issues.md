---
title: "Very irritating mdadm issues"
date: 2012-03-21
forum: General Help
---

### Post by jimbolaya on 2012-03-21
I'm running 32-bit 10.04 LTS.

I've been having a great deal of frustration setting up a mirrored mdadm RAID on my box.  I've wasted a lot of time.

For a long time, I ran a RAID on bare disks, no partitions.  Having had some issues with that and reading that it's probably better to use partitions, I created partitions on the disks in question:

```
Disk identifier: 0x6dc3a84a
   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      765634  1953513560   fd  Linux raid autodetect

Disk identifier: 0xad29671f
   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      765634  1953513560   fd  Linux raid autodetect
```

OK, now to create the RAID:

```
root@shenandoah:~# mdadm -Cv /dev/md1 -l1 -n2 /dev/sd[jg]1
mdadm: size set to 1953513472K
mdadm: array /dev/md1 started.
root@shenandoah:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdj1[1] sdg1[0]
      1953513472 blocks [2/2] [UU]
      [>....................]  resync =  0.0% (432064/1953513472) finish=527.3min speed=61723K/sec

root@shenandoah:~# mdadm --detail --scan | grep md1
ARRAY /dev/md1 level=raid1 num-devices=2 metadata=00.90 UUID=8d8198de:c9da8301:a71f119f:8257d0d2
```

Wait for the array to finish resyncing:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdj1[1] sdg1[0]
      1953513472 blocks [2/2] [UU]
```

Good, done.  I read that I might want to rebuild initrd:

```
mkinitramfs -o /boot/initrd.img-2.6.32-39-generic-pae 2.6.32-39-generic-pae
```

Reboot.  Then take a look at the RAID disks:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdk[0] sdn[1]
      1953513472 blocks [2/2] [UU]
      
md3 : active raid1 sda2[0] sdb2[1]
      37110080 blocks [2/2] [UU]
      
md2 : active raid1 sda3[0] sdb3[1]
      156296320 blocks [2/2] [UU]
      
md0 : active raid1 sde1[1] sdc1[0]
      488383936 blocks [2/2] [UU]
      
md6 : active raid1 sdh1[0] sdj1[1]
      976759936 blocks [2/2] [UU]
      
unused devices: <none>
```

Crap!!  /dev/md1 is now the bare disks.  Let's look at the md devices:

```
root@shenandoah:~# ls /dev/md1*
/dev/md1  /dev/md1p1
```

What automatic process (this sort of thing shouldn't be an automatic, dynamic naming process) is doing this?  Why doesn't it honor the mdadm.conf?  I've tried looking around to try to turn this off or make it do what I want.  If it's doing this to a new array, why doesn't it foobar the old ones (which would be really really bad, not just a waste of time and annoying).

---

