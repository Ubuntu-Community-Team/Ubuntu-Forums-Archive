---
title: "Having trouble moving non-system RAID1 to fresh install"
date: 2010-03-07
forum: General Help
---

### Post by stargazera5 on 2010-03-07
I had a system with a softRAID 1 non-system array (ie. Data only with system partition on separate disk).  Unfortunately the system got hosed when running some long delayed patches.  It got to the point where a full reinstall was needed.  I've got the new system up with mdadm and lvm2 installed (not sure if the latter is needed?).  Unfortunately I can't seem to get the system to recognize my RAID 1 array.

The disks are on sda and sdc:
```
root@Draco:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e819b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00068bd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15024   120680248+  83  Linux
/dev/sdb2           15667       15810     1156680   82  Linux swap / Solaris
/dev/sdb3           15811       23821    64348357+  83  Linux
/dev/sdb4           23822      121601   785417850    5  Extended
/dev/sdb5           43225      121601   629563221   83  Linux
/dev/sdb6   *       23822       42431   149484762   83  Linux
/dev/sdb7           42432       43224     6369741   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00060ccb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

```

/dev does not list the partitions:
```
ls /dev/sd*
/dev/sda
/dev/sdb
/dev/sdb1
/dev/sdb2
/dev/sdb3
/dev/sdb4
/dev/sdb5
/dev/sdb6
/dev/sdb7
/dev/sdc

```

When I try to use mdadm, here are the results:
```

root@Draco:~# mdadm --assemble --scan
mdadm: No arrays found in config file or automatically
root@Draco:~# mdadm --detail --scan --verbose
root@Draco:~# mdadm --detail --scan
root@Draco:~# mdadm --examine --scan /dev/sda1 /dev/sdc1
root@Draco:~# mdadm --assemble --scan --auto-update-homehost
mdadm: No arrays found in config file

```

I think I'm missing something, but no amount of searching online has helped me to figure it out.  Help?

StargazerA5

---

### Post by rocknrollmouse on 2010-03-07
What is the output from:

cat /proc/mdstat

---

### Post by stargazera5 on 2010-03-07
> **rocknrollmouse said:**
> What is the output from:

cat /proc/mdstat

```

root@Draco:~# cat /proc/mdstat
Personalities : 
unused devices: <none>
root@Dravo:~#

```

StargazerA5

---

### Post by stargazera5 on 2010-03-11
Anybody have any ideas?

StargazerA5

---

### Post by stargazera5 on 2010-03-13
Okay, a bit more info:

The RAID array was originally made under Jaunty 64 bit, which had no trouble recognizing the disks (see below).  The fresh install was of Karmic 64 bit.  I should have mentioned this earlier when explaining the reinstall, but :oops:

Anyway, I burned off a disk of Jaunty 64 bit, and it recognized the partitions (emphasis added by me to note the RAID partitions Karmic did not detect):

```

root@ubuntu:~# ls/dev/sd*
/dev/sda    /dev/sdb    /dev/sdb2   /dev/sdb4   /dev/sdc
_**/dev/sda1**_   /dev/sdb1   /dev/sdb3   /dev/sdb5   _**/dev/sdc1**_
root@ubuntu:~#

```

Attempting to mount a partition gave the following, which I think is expected:

```

root@ubuntu:~# mount /dev/sda1 /home/ubuntu/Desktop/raid
mount: unknown filesystem type 'linux_raid_member'
root@ubuntu:~# mount /dev/sda1 /home/ubuntu/Desktop/raid -t ext3
root@ubuntu:~#

```

I was able to access all the files!

Since this isn't a permanent installation, I haven't tried detecting the array yet, but given that I can access the disks, I think it would work.  Is there a regression from Jaunty to Karmic regarding this?  I think the fact that Jaunty seems to recognize sda1 and sdc1 but Karmic doesn't suggests this.  Unfortunately my google-fu didn't turn up anything, but hopefully somebody in the forums can point me in the right direction.

What I need is to get the array working in Karmic.  Right now the main option I can see is to go from backup and recreate the array in Karmic from scratch ](*,) Anybody have any better ideas?

StargazerA5

---

### Post by stargazera5 on 2010-03-30
This issue was resolved in a bug ticket:
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/538597](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/538597)

Dmraid was preventing Ubuntu from properly recognizing the disks.  Removing it and rebuilding initramfs resolved the issue, see link above.

StargazerA5

---

