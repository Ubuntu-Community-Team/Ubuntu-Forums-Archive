---
title: "Migrating to RAID 1"
date: 2012-10-12
forum: General Help
---

### Post by VeeDubb on 2012-10-12
I'm trying to migrate the drive containing /home to a raid 1, and I've found so many incomplete and wildly divergent instructions I'm not sure where to start, other than spending the next 6 months studying raid and playing around in VBox.

Right now, I have a 3 harddrives.

sda (160GB) with / at sda1, plus a swap partition.

sdb (1TB) for /home at sdb1 (only partition on drive)

sdc (1TB) not in use, but formatted with a single ext4 the same size as sdb1.


I have a motherboard that has a basic RAID controller that can handle raid 1, but there is absolutely zero documentation for it, even from the manufacturer.  So, software raid using mdadm seems like a better option.

My goal, is to convert sdb and sdc to a mirrored raid1 array so I have built in data redundancy, but to do so without losing my data.


The best I've cobbled together from different how-to's would be to tell the computer that sdb1 is part of a raid 1 using:
```
mdadm --create /dev/md0 -n 2 -l 1 /dev/sdb1 missing
```


...and then add sdc1 to the array using:
```
mdadm --manage /dev/md0 -a /dev/sdc1
```

...and then modify my fstab to mount md0 as the new /home.



But that leaves me with a lot of questions.

[LIST=1]
[*]Will this even work the way I've described?
[*]Will this be non-destructive to my data, aside from the usual disclaimers?
[*]Can this be done on a live system?
[*]Just precisely how do I modify my fstab to mount the array?  Is it as simple as changing all references to sdb1 to md0?
[*]I know that raid 1 is supposed to have increased read performance in addition to the obvious benefit to data safety, but is that still true of a software raid set up through mdadm? (not a deal breaker, just curious)
[/LIST]

Again, please note that /home is on it's own physical disk.  I don't want or need to move/copy/duplicate the OS.  In my particular setup, having my / partition fail is a minor inconvenience.  Losing /home would be catastrophic if not for my backups, but would still be a huge pain, even with them.

---

### Post by VeeDubb on 2012-10-12
So I've attempted this in a VM, and it's not working, but may be still recoverable. 

I booted the VM in root recovery, issued the commands above to create the array and then add a disk to it, and 'attempted' to modify my fstab.  All I did was replace the UUID disk reference in my fstab with /dev/md0, which obviously was not the solution.

On reboot, the array wouldn't mount.  

mdadm --examine --scan   returns```
ARRAY /dev/md/0 metadata-1.2 UUID=theusualgibberish name-raidtest:0
```

From that I assumed the dev for the array was at /dev/md/0 and modified the fstab accordingly.  No dice.

On inspection, it appears that /dev/md0 and /dev/md/0 are both non-existent.  

Where do I go from here?

---

### Post by dcstar on 2012-10-13
[https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID)

---

### Post by VeeDubb on 2012-10-13
Thanks for the link.  It's not quite what I'm looking for, since / and /home are on separate physical drives and only /home is going into the raid array, but it seems a lot more coherent than a lot of the how-to's I've seen, so I can quite possibly make a go of it.

---

### Post by VeeDubb on 2012-10-14
I ended up finding these direction -> [http://ubuntuforums.org/showthread.php?t=1832812](http://ubuntuforums.org/showthread.php?t=1832812) which were quite a bit more usable, although still aimed at moving your entire system to raid1.  It was fairly straight forward to simplify the process for using it to move /home to a RAID1.  It basically just meant using real mount points instead of making arbitrary ones, and skipping the entire section on grub, since my boot device was left untouched.

To anyone else who finds this, if you're only moving a secondary partition to raid, and NOT your /, the whole thing can be done easily from a live system with only 1 reboot.  The only thing in the directions that didn't work for me at all was the command to add the second disk to the array, but I was able to do that with a great deal more confidence that I was doing it correctly by using the Disk Utility anyway.

---

### Post by VeeDubb on 2012-10-15
This is not as solved as I thought it was.

Everything went fine, and the array started rebuilding after I added the 2nd disk, but it apparently started adding it as a spare.  Right now, this is what I get when I query the array:

```
stephen@Bear-Desktop:~$ sudo mdadm --query --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Sat Oct 13 00:34:53 2012
     Raid Level : raid1
     Array Size : 976629568 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976629568 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Oct 15 09:40:29 2012
          State : clean, degraded, recovering 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 1% complete

           Name : Bear-Desktop:0  (local to host Bear-Desktop)
           UUID : 6ec51b17:0ec5f4bb:0e5dfadc:953b31e1
         Events : 55809

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       2       8       17        1      spare rebuilding   /dev/sdb1

```

I've tried removing and re-adding the 2nd disk several times, but it keeps coming up as a spare instead of an active part of the array, so the array continue shows up degraded.  I've looked all over for a solution, but I can't seem to find one.

Any help?

---

### Post by Slim Odds on 2012-10-15
> **VeeDubb said:**
> This is not as solved as I thought it was.

Everything went fine, and the array started rebuilding after I added the 2nd disk, but it apparently started adding it as a spare.  Right now, this is what I get when I query the array:

```
stephen@Bear-Desktop:~$ sudo mdadm --query --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Sat Oct 13 00:34:53 2012
     Raid Level : raid1
     Array Size : 976629568 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976629568 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Oct 15 09:40:29 2012
          State : clean, degraded, recovering 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 1% complete

           Name : Bear-Desktop:0  (local to host Bear-Desktop)
           UUID : 6ec51b17:0ec5f4bb:0e5dfadc:953b31e1
         Events : 55809

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       2       8       17        1      spare rebuilding   /dev/sdb1

```I've tried removing and re-adding the 2nd disk several times, but it keeps coming up as a spare instead of an active part of the array, so the array continue shows up degraded.  I've looked all over for a solution, but I can't seem to find one.

Any help?
Did you give it some time? It says that it's 1%.... does that increase later?

---

### Post by VeeDubb on 2012-10-15
Never mind.  After all the trouble, it turns out the spare 1TB drive I got has a few bad sectors, and while the drive is still perfectly functional, it's causing errors syncing the array, which is why it keeps coming up as a spare.  At least now I know how to do it...

---

### Post by VeeDubb on 2012-10-15
> **Slim Odds said:**
> Did you give it some time? It says that it's 1%.... does that increase later?

I gave it about 4.5 hours several times over.  Each time it got all the way up to 100 percent, but the drive still showed up as degraded, and the 2nd drive showed up as a fully synced spare instead of an active member.  I tried rebooting, thinking that restarting the array would mark it active, but on reboot, it still said degraded and started the sync all over again.

I'm feeling reasonably confident that the bad sectors are to blame, although if you've got another idea, I'd love to hear it.  It doesn't seem like a few bad sectors should be a deal breaker.

---

### Post by Slim Odds on 2012-10-15
> **VeeDubb said:**
> I gave it about 4.5 hours several times over.  Each time it got all the way up to 100 percent, but the drive still showed up as degraded, and the 2nd drive showed up as a fully synced spare instead of an active member.  I tried rebooting, thinking that restarting the array would mark it active, but on reboot, it still said degraded and started the sync all over again.

I'm feeling reasonably confident that the bad sectors are to blame, although if you've got another idea, I'd love to hear it.  It doesn't seem like a few bad sectors should be a deal breaker.
It does sound like the bad sectors were the problem. Since you're using RAID1 as essentially a hard drive mirror, all of the physical parts of the drive are duplicated. Since one drive can't do that, it's a failure condition.

---

