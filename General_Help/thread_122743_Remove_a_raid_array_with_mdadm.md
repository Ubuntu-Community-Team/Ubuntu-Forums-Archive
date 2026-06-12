---
title: "Remove a raid array with mdadm"
date: 2006-01-28
forum: General Help
---

### Post by tomatchili on 2006-01-28
I've managed to start some arrays with mdadm as a test, but I do not want them anymore! How do I remove them? mdadm --stop /dev/md0 seems to only remove it until a new reboot.

---

### Post by golfinguy on 2006-03-30
Wanted to bump this one, as I have the same question and cannot seem to find the answer.

Anyone?

---

### Post by Stormbringer on 2006-03-30
If I'm not completely mistaken ...

# mdadm --manage --stop /dev/mdX
To stop the RAID set.

Replace the "X" with the number of the RAID-set you want to stop (md0, md1,...).

Delete the partitions on the RAID drives or change their partition ID to 83 (linux).

See if there's a mdadm.conf inside of /etc ... delete it.

That should do the job.

Storm.

---

### Post by golfinguy on 2006-03-30
Oh I agree - that *should* do the job.  However......

I've stopped the array, removed the partitions from the drives, and made sure there was no mdadm.conf.  Upon rebooting however - it STILL sees the damn array!  I'm at a loss as to how.

Whats interesting is that the reason I wanted to start over is because I made a mistake the first time (didn't create any partitions before adding drives to the array) and it told me /dev/sdb was faulty.  The drives are all brand new so I figured it was my mistake that fouled it up.  HOWEVER, upon rebooting and the array still thinking it was there - it now lists /dev/sda as faulty and /dev/sdb as active and sync.   ????

I'm losing my feeble mind here.  I just wanted to start anew and do not seem to be able to.  Even tried creating /dev/md1 and it just tells me the drives appear to be part of an array already (even after the 'stop').  I tell it to go ahead, and it does the same thing - /dev/sdb faulty.  I was able to stop and remove that one though - it doesn't show up anymore.

stop, make sure partitions are gone, no mdadm.conf, reboot just to be sure - and here we are again - the damn thing won't go away (back to /dev/sda faulty - /dev/sdb good):


[FONT="Courier New"][I]root@rahserver:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Thu Mar 30 10:06:27 2006
     Raid Level : raid5
     Array Size : 1172133888 (1117.83 GiB 1200.27 GB)
    Device Size : 390711296 (372.61 GiB 400.09 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar 30 02:11:52 2006
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : fcf690a6:a5621c27:74357af6:eed076dd
         Events : 0.41

    Number   Major   Minor   RaidDevice State
       0       0        0        -      removed
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       0        0        -      removed

       4       8        0        -      faulty   /dev/sda
       5       8       48        -      spare   /dev/sdd[/I]
[/FONT]


Brain melting............. sleepy.......................... goin to bed.

---

### Post by Stormbringer on 2006-03-30
Ok, Ubuntu seems to work a little different than I'm used too ... my server is currently still running CentOS, but it's scheduled to be replaced with the Dapper Server upon availiability.

However...

- Inside of /etc is a directory called mdadm ... should be empty.
- Look out for /etc/raidtab ... if exists, delete the thing.
- Take a look into /etc/defaults.d ... maybe mdadm stores the one or another file there too.

Getting rid of a RAID in Ubuntu seems to be tough work ...

Storm.

---

