---
title: "Request for hand holding on upgrade to 10.04 (re: RAID)"
date: 2010-06-12
forum: General Help
---

### Post by DrBloodmoney on 2010-06-12
Currently I have a headless box that sits in the basement running Ubuntu Desktop 9.04.  I mostly administer it via SSH.  I want to upgrade this box to 10.04, but also switch from Desktop to Server. This machine contains an array with non-critical data that would be a pain in the posterior to lose, but not a big deal (mostly media, ripped DVD's and the like).

My question is regarding the software (mdadm) raid on the machine.  Can I expect it to just work after installing 10.04 onto a non-raid disk?  Any pitfalls to watch out for?

```

lanserver@lanserver:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sde1              46G   28G   17G  64% /
tmpfs                 1.6G     0  1.6G   0% /lib/init/rw
varrun                1.6G  420K  1.6G   1% /var/run
varlock               1.6G     0  1.6G   0% /var/lock
udev                  1.6G  168K  1.6G   1% /dev
tmpfs                 1.6G     0  1.6G   0% /dev/shm
lrm                   1.6G  2.2M  1.6G   1% /lib/modules/2.6.28-18-generic/volatile
/dev/md0              2.7T  472G  2.1T  19% /mnt/raid
/dev/sde3              93G   21G   68G  23% /mnt/Backup

```

```

lanserver@lanserver:~$ blkid
/dev/sde1: UUID="91ac93b8-292b-4534-8eb8-652672bf06ad" TYPE="ext3" 
/dev/sde5: TYPE="swap" UUID="ed573b39-b961-421c-8007-74fd7339d965" 
/dev/sda1: UUID="f3852f12-3523-7264-1201-a31125bb6caa" TYPE="mdraid" 
/dev/sdb1: UUID="f3852f12-3523-7264-1201-a31125bb6caa" TYPE="mdraid" 
/dev/sdc1: UUID="f3852f12-3523-7264-1201-a31125bb6caa" TYPE="mdraid" 
/dev/sdd1: UUID="f3852f12-3523-7264-1201-a31125bb6caa" TYPE="mdraid" 
/dev/sde3: UUID="8672aaad-ae18-4ce1-b429-563b6ae46c4f" TYPE="ext3" 
/dev/md0: UUID="00a10a4d-c0d7-4141-a8e1-7e6b14ca4fa3" TYPE="ext3"

```

```

lanserver@lanserver:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[3] sdc1[2] sdb1[1] sda1[0]
      2930279808 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

---

### Post by DrBloodmoney on 2010-06-12
Bump

---

### Post by aphatak on 2010-06-12
I recently updated two servers from 8.04 LTS to 10.04 LTS; each of these servers has a RAID5 array, managed by mdadm, and exported via NFS.  On the first boot of 10.04, the array was recognized and started.
I am paranoid, so I did not really 'upgrade'.  I installed 10.04 LTS in another partition (that way I could go back to running 8.04 if 10.04 bombed).  When 10.04 started up, I logged in and copied old configuration files (for example /etc/samba/smb.conf, /etc/network/interfaces, and /etc/exports) from the 8.04 partition.  Another restart, and that was it.
If you had the desktop environment, and do not want it on upgrade, installing 10.04 in another partition is what I would recommend to keep the old gluteus maximus covered!

---

### Post by aphatak on 2010-06-28
Did your upgrade work?

---

