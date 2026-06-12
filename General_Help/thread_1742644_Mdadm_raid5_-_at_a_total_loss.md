---
title: "Mdadm raid5 - at a total loss"
date: 2011-04-29
forum: General Help
---

### Post by steven6282 on 2011-04-29
I really can't figure this thing out.  It doesn't make any sense to me why it's doing what it's doing.

I previously installed ubuntu and created a raid 5 software array using mdadm.  Had a few things on it but then needed to change the hdd I had ubuntu installed on as I was using an external drive for testing purposes.

Well I reinstall ubuntu on a new drive, and now I can't get the raid to set up correctly.  I've already blown away all the data on it, thats not important, but I can't even create the array from scratch correctly again.

I've got 3 drives /dev/sdb /dev/sdc and /dev/sdd that I want to add to the array.

Following some guides and like I did before that worked I created partitions on each drive and set the type to linux raid auto detect.

I then did this:

mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

No matter what I try it always creates the raid with 2 of 3 drives, and puts the 3rd as a spare.  I've even tried setting --spare-devices=0 in the create statement to no avail.

I've zero'd out the superblock on all the drives, have fdisked them and formatted them clean multiple times and no matter what I try this is what keeps happening.

Can someone please help me make some sense out of this?

Thanks.

---

### Post by sj1410 on 2011-04-29
a pretty simple explanation here

[http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html](http://blog.swapnil.me/2011/01/simple-recipe-to-create-raid5-under.html)

---

### Post by steven6282 on 2011-04-29
Thanks for the link, but that looks to be just a simple guide on how to set up the raid.  I've gotten way beyond those simple steps and am having an actual problem that that article does not address in any way.  I even said I had the raid set up on another install previously, that should demonstrate that I know the simple steps to creating it.  It's just doing something abnormal here that is throwing me for a loop and to which I'm asking for help on.

Also for the record I'm using ubuntu server so can't use GUI software like gpart.  I did however use fdisk to set the disks up in the same way that article is talking about.

---

### Post by steven6282 on 2011-04-29
*sigh* this really makes absolutely no sense...
 
I wiped everything away again. Did a brand new fresh install. Zero'd out the superblocks, deleted all partitions.. everything.
 
Took these exact steps:
 
fdisk /dev/sdb
created primary partition 1 using all the space
set the type to fd
wrote the partition table
repeated for sdc and sdd
 
mdadm --create /dev/md0 --level=5 --spare-devices=0 --assume-clean --raid-devices=3 /dev/sd[bcd]1
 
Created the array fine. 3 of 3 drives
 
mke2fs -j /dev/md0
 
Formatted fine no problems.
 
mount /dev/md0 /mnt/raid
 
mounted fine
 
dd if=/dev/zero of=/mnt/raid/5g bs=1M count=5120
 
Wrote to the array fine no problem
 
mdadm --detail /dev/mdo 
```

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb1
       1       8       32        1      active sync   /dev/sdc1
       2       8       48        2      active sync   /dev/sdd1

```
 
echo DEVICE partitions > /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
 
Doubl checked by doing:
mdadm --stop /dev/md0
mdadm --assemble /dev/md0
 
Everything still looks good.
 
 
 
Reboot the computer and all goes to crap again
 
Array comes online with 2 of 3 drives
 
mdadm --detail /dev/md0
```

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       3       8       48        2      spare rebuilding   /dev/sdd

```
 
 
*sigh* WHY......
 
EDIT:
 
more info... I stopped it and tried re assembling it after rebooting and one time it worked.  Rebooted again same problem it showed the third device as a spare.  Stopped it again and re assembled it this time it shows sdb1 and sdc1 but shows the 3rd device as removed.
 
Also notice, when rebooting it is building the array with the devices not the partitions.  When I stop and reassemble it it uses the partitions.  And somehow sdd1 is now completely gone...
 
 
This raid array worked fine yesterday and had been working for 5 days on another install... I just don't get how it can be having so many problems creating it now.

---

### Post by steven6282 on 2011-04-29
One more update,
I think I may have gotten it working correctly now. It has correctly loaded the array as it should through 10 reboots now.
 
I did a aptitude full-upgrade and it upgraded 57 packages. Not sure what all packages it upgraded, but something must've been effecting it cause it seems to be working now.
 
EDIT:
 
Nevermind still not working right. Tried to remove a file from the raid device (could see the test files I wrote to it listed) and it locked up something. Could not even kill -9 the rm command. Rebooted again and now it's not creating the array correctly again.
 
*sigh*
 
I'd almost think it might be a hardware problem if the hardware wasn't brand new and works perfectly fine if I'm not using it in a raid array.  If I just format each of my 3 disks and use them as single drives they work perfectly fine.

---

