---
title: "Ubuntu Desktop and RAID 1"
date: 2009-07-22
forum: General Help
---

### Post by malfist on 2009-07-22
I finally ran out of room on my 250 GB harddrive so I bought a second 750 GB harddrive (I already had one for use as a backup). Now I want to set my two 750 GB harddrive up as RAID1 but can't seem to do that.

I downloaded the AMD64 Alt install CD for 9.04, but when I go to manually configure the partition, there is no option for raid. 

What do I need to do to get RAID on my desktop?

---

### Post by discodan on 2009-07-23
Booting from Raid 1 can be a bit tricky, but here's how I have done it in the past.

Using the alt install cd is the right choice.

When you get to the partitioning screen choose manual, as you stated.

Now, You'll need 2 partitions on each drive.  Assuming these are sata drives, they will probably be /dev/sda and /dev/sdb.  if so, we are attempting to create /dev/sda1, /dev/sda2, /dev/sdb1, and /dev/sdb2.

/dev/sda1 and /dev/sdb1 will combine to form a raid1 for /
/dev/sda2 and /dev/sdb2 will combine to form a raid1 for swap

to start with, decide how much space you want dedicated to swap.  If it were me, I would allocate something like 740 GB for / and 10 GB for swap.  But really it's up to you.

So, assuming you go with the 740 GB / and the 10 GB swap.  Create your partitions on /dev/sda as follows:

1st partition - 740 GB - boot flag on - type Linux Raid
2nd partition - 10 GB - no boot flag - type Linux Raid

Don't forget the boot flag on the first partition... it's important

Then repeat this on /dev/sdb.

Again don't forget the boot flag on the first partition of /dev/sdb... this one is also important

If you did it right, you should have a new option at the top of the partitioning screen to configure raid :)

Choose this option.  You should be prompted to save the changes you made to  /dev/sda and /dev/sdb.

Now, if memory serves, on the next menu, you will need to create a new md device.  I think md stands for multi-disk.  Choose raid1, then select to include /dev/sda1 and /dev/sdb1.  The way you choose these is by highlighting your choices with the cursor keys and hitting your spacebar to put an X in the box next to the partition you want included in the array.  Then hit tab to and enter to save or finish the array.

Now do this again from the create new md device screen for /dev/sda2 and /dev/sdb2.

Finally choose the option to finish and go back to the partitioning screen.   *sorry I don't remember the exact phrasing on the menus.  But, I think you'll figure it out.*

Ok, now you should be back at the partitioning screen, but now you have 2 new items listed at the top.  These are the newly created SW Raid arrays.  Select the 740GB array and choose to the filesystem and mount it to /.  For 740GB, I would use XFS, but that's also your choice.  Then select the 10GB array and choose to use it for swap.

Then choose to finish, and the setup should continue as normal.  

Now here's the part where it gets a little weird.  In my experience, when you get to the end of the install, and the cd ejects, and you're prompted to reboot.  Don't reboot...  I don't know if it's just me, but every time, I reboot right away, there is all kinds of chaos when ubuntu tries to boot for the first time.  Since I have never read anything about this in any of the RAID howtos, It really could be just me.  But I have built several Ubuntu servers recently of varying HW, and they all behaved the same.  If I reboot when prompted, It's not good.  So here's what I do:

When prompted to reboot, choose the option to go back.  Scroll around till you find the option to dump to a shell.

From here you will be watching for your new arrays to sync for the first time.  See, after you create an array for the first time, the drives in the array have to sync up.  And that 740GB array could take 2-3 hours for this to occur.  The command you use to monitor the sync is mdadm.

Your two new arrays should be named /dev/md0 (this one should be the 740GB /) and /dev/md1 (this one should be the 10GB swap).

So to check the status of the 740 GB array, type:

```
mdadm --detail /dev/md0
```

also to check the status of the 10GB array, type:

```
mdadm --detail /dev/md1
```

The sync status should be listed as a % towards the bottom of the output.  Once both arrays are sync'd and "clean" you can finally reboot.

```
shutdown -r now
```

Hope this helps.  If you have any questions, please post, and I'll happily help.  Like I said, I've done this a lot lately setting up samba servers at the office.  Also, sorry I don't remember the exact menu choices during the install procedure. If you need these let me know.

-disc-

---

