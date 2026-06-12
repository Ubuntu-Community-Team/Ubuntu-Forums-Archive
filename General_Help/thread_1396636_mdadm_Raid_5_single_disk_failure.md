---
title: "mdadm Raid 5 single disk failure"
date: 2010-02-02
forum: General Help
---

### Post by slapnutz on 2010-02-02
I've had a Raid 5 running on my ubuntu box for about a year.

Recently, one the SMART utility said that one of the drives had failed and another drive was about to fail. I downed the box and hooked them up to my windows machine to run sea tools on them (They are all seagate drives). Sea Tools said that the drives were fine, while ubuntu said they were failing/dead.

Yesterday I decided to try to fix one of the drives in the raid. I turned the server off, took the failed drive out, and restarted. Of course the raid didn't work because only 2 of the 3 drives were there, however it had been working w/ only 2 of the 3 drives for a couple months now (I'm a lazy college student). I turned it back off and back on with the drive there just to see if I could get the raid up again, but I havn't been able to get it to go. So far I've tried:

```

mdadm --assemble /dev/md0 /dev/sd[b,c,d]

mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted


mdadm --assemble --force /dev/md0 /dev/sd[b,c,d]

mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted

 mdadm --create /dev/md0 --level=raid5 --raid-devices=3 /dev/sd[b,c,d]

mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=3 ctime=Thu Feb 12 15:40:41 2009
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=3 ctime=Thu Feb 12 15:40:41 2009
Continue creating array? y
mdadm: ADD_NEW_DISK for /dev/sdb failed: Invalid argument

```

I've looked around some other forums and realized the next logical question/request is for mdadm -E on all of the drives:

```

mdadm -E /dev/sd[b,c,d]
mdadm: No md superblock detected on /dev/sdb.
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 31b6a82f:d9866820:a4de4c44:2187b897
  Creation Time : Thu Feb 12 15:40:41 2009
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 976772992 (931.52 GiB 1000.22 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Feb  2 09:17:36 2010
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 2d4693f8 - correct
         Events : 3088579

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       32        0      active sync   /dev/sdc

   0     0       8       32        0      active sync   /dev/sdc
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 31b6a82f:d9866820:a4de4c44:2187b897
  Creation Time : Thu Feb 12 15:40:41 2009
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 976772992 (931.52 GiB 1000.22 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sun Jan 31 17:13:00 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 2d446061 - correct
         Events : 3088574

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       48        1      active sync   /dev/sdd

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       48        1      active sync   /dev/sdd
   2     2       0        0        2      faulty removed


```

I know that this is a long winded post, but I'm looking for a way to trick the raid into working with just 2 drives until I can warranty the seagate and buy an external 1.5 TB drive to use as another backup. 

If anyone has any suggestions please let me know. If you don't know how to fix this, then instructions or a link to instructions on how to remove the bad drive from the array and replace it with a fresh drive, without data loss, would be greatly appreciated.

Thanks,
~Mike

---

### Post by zabby39103 on 2010-06-27
This is pretty much exactly my problem, I figured I'd bump rather than create a new post - can anyone help?

I was googling about this, and I found an article on [Linux Online]("http://www.linux.org/docs/ldp/howto/Software-RAID-0.4x-HOWTO-4.html").

It had a section on this, but... I quote
> Even if one of the disks has failed, you still have to mdadd it as you would in a normal setup. (?? try using /dev/null in place of the failed disk ??? watch out) 

All those question marks and the "watch out" doesn't really fill me with confidence.  

Also can someone recommend a good RAID 5 recovery tutorial?  I did some googling, and they tend to be really old or written for someone that has more linux knowledge than I do.

---

### Post by slapnutz on 2010-06-27
If you read the mdadm wiki somewhere it says something about 'In the more current versions, an N-disk Raid 5 is capable of working w/ just N-1 disks.' That is what I did until I was able to get a new drive and just add it back in. I then realized linux software Raid was crap (Ok not so much linux's, all software raids are crap, but linux atm is one of the most lacking) and twonky/ushare weren't playing nicely enough w/ my XBox and switched over to Windows Home Server. 

Eventually I do want to get a hardware Raid controller and reinstall Linux to go with something like Myth or Boxee, but lacking in the $$ :(.

---

### Post by dino99 on 2010-06-27
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

