---
title: "RAID &quot;Check Array&quot; command"
date: 2010-12-17
forum: General Help
---

### Post by SaturnusDJ on 2010-12-17
What is the terminal command to check an array? Disk Utility does have a button "Check Array" for this.

```
mdadm --assemble /dev/mdx --update=resync
```
Does not work because the array is already running of course.


[https://secure.bonkabonka.com/blog/2008/02/10/checking_an_mdadm_array.html](https://secure.bonkabonka.com/blog/2008/02/10/checking_an_mdadm_array.html)
Does not work either.

Could not find anything in the man except for '--assume-clean' but this doesn't seem to do it either.

---

### Post by rubylaser on 2010-12-17
What do you mean the check option doesn't work?  By default this is the value of the sync_action

```
root@fileserver:~# cat /sys/block/md0/md/sync_action 
idle

```
If you pass it the echo check...
```
echo check > /sys/block/md0/md/sync_action
```
```
root@fileserver:~# cat /sys/block/md0/md/sync_action 
check

```

```
Every 2.0s: cat /proc/mdstat                            Fri Dec 17 17:45:48 2010

Personalities : [raid6] [raid5] [raid4]
md0 : active raid6 sdb1[0] sdf1[7] sdh1[6] sdi1[5] sdg1[4] sdc1[3] sdd1[2] sde1[
1]
      5860558848 blocks level 6, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]
      [>....................]  check =  0.2% (2438896/976759808) finish=263.7min
 speed=61561K/sec

unused devices: <none>

```

It will check the array.  Works fine for me.

```
root@fileserver:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sun Aug  1 16:26:04 2010
     Raid Level : raid6
     Array Size : 5860558848 (5589.06 GiB 6001.21 GB)
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Dec 17 17:31:01 2010
          State : clean, recovering
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 0% complete

           UUID : d4e58776:640274d8:e368bf24:bd0fce41
         Events : 0.16736

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       65        1      active sync   /dev/sde1
       2       8       49        2      active sync   /dev/sdd1
       3       8       33        3      active sync   /dev/sdc1
       4       8       97        4      active sync   /dev/sdg1
       5       8      129        5      active sync   /dev/sdi1
       6       8      113        6      active sync   /dev/sdh1
       7       8       81        7      active sync   /dev/sdf1

```

---

### Post by rubylaser on 2010-12-17
You just want to make sure once it's checked that the mismatch count is 0.
```
root@fileserver:~# cat /sys/block/md0/md/mismatch_cnt
0

```

---

### Post by rubylaser on 2010-12-17
Finally, the --assume-clean option is used when forcing an array back together and it's not being cooperative.  If you know it's clean, you can use that option.  Hope that clears that up a litte.

---

### Post by SaturnusDJ on 2010-12-17
Thanks. I dont use the kind of commands coming from the link I posted.

```
:~$ sudo echo check > /sys/block/md1/md/sync_action 
bash: /sys/block/md1/md/sync_action: Permission denied

```

---

### Post by rubylaser on 2010-12-17
Can you make yourself a full time root user like this...
```
sudo -i
```

Then paste the output of
```
cat /sys/block/md1/md/sync_action
```

If that returns idle, can you try
```
echo check > /sys/block/md1/md/sync_action
```

If it doesn't return idle can you paste the output of
```
mdadm --detail /dev/md1
```

Or better yet
```
mdadm --detail --scan
```
Thanks

---

### Post by SaturnusDJ on 2010-12-17
The disk state is ok, but I was searching for this command. Trying to gain more RAID knowledge as you know.
After
```
sudo -i
```
the 'force' to check command works.

1. Is there a way to execute this command without becoming root first?
Edit: ```
sudo su - -c 'echo check > /sys/block/md0/md/sync_action'
```
Does work now...hmmm, really thought I triple checked for typo's before posting this topic...


2. And what is the 'story' behind it, why is mdadm missing a 'check option'?

:)

---

### Post by rubylaser on 2010-12-17
No, you have to become root in some fashion to execute commands on block devices (that's what mdadm is).  The command I gave you just switches you permanently to the root user.

This command...
```
sudo su - -c
``` Uses sudo to allow your user to run the command su - which lets you run the command (-c) in the quotes as the root user.  So, to make a long story short, you have to be the root users to pass any options to the various parameters of an mdadm array.

---

### Post by rubylaser on 2010-12-17
I'm not sure what you mean by missing the check option... When you pass echo check to the array, it checks the array, that's why it will return check after you run this command.
```
root@fileserver:~# echo check > /sys/block/md0/md/sync_action
```

It checks the array for consistency and once it's done, you'll notice that value will return back to idle, because it's no longer "checking" the array.

---

### Post by SaturnusDJ on 2010-12-17
Seems to work nice indeed, but I expected something like "mdadm --manage /dev/mdx --check" or so...wonder why they didn't give mdadm such an option.

---

### Post by rubylaser on 2010-12-17
Not sure why it's not in mdadm, but you can pass all sorts of values to block devices, including all of the items in /sys/block/md0/md.  If you use cat on alot of them, you'll see values.  You can set read_ahead on individual drives like this.
```
echo 1024 > /sys/block/sdb/queue/read_ahead_kb
``` 
or read ahead for an array
```
blockdev --setra 65536 /dev/md0
```
or stripe cache size
```
echo 16384 > /sys/block/md0/md/stripe_cache_size
```

All of these options can greatly effect performance, but researching each value and understanding it before you change it is critical.

---

### Post by SaturnusDJ on 2010-12-18
A nice, some advanced stuff. Will play around with it in a safe (VM) environment.

---

