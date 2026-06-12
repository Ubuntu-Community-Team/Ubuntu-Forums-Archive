---
title: "RAID5 install issues using xubuntu 10.10 alternate"
date: 2011-09-23
forum: General Help
---

### Post by chipppy on 2011-09-23
Good Morning

On a RAID5 install how do i fix
error: disk out of space
grub rescue>


I am trying to setup a RAID system via the Xubuntu 10.10 64bit alternate, using5 X 2TB HDD's to create a RAID5 setup
I have tried the same configeeratin both via GParted and via the install CD's partition system.

Each Hdd split to 
1mb free (I am assuing this is the MBR space)
100mb bios grub
1000mb swap
rest <2TB data
72.8kb free (it just a lazy few kb doing nothing)

Then RAID5 the swap and data partitions. the bios grub is left seperate for grub to be installed into.

When I setup this via GParted I used the GPT partition table and had to use the instll Cd to setup the RAID5

All times I have tried this the install goes well and the bootloader is installed on to all 5 HDD's.  The install goes asper a normal install (I did a single HDD install to see if something different happened and it was all the same)

When I reboot the following comes up as the computer boots

verifying DMI pool data............
error out of disk
grub rescue>_

I did a search and this error seems to refer to a legacy issue to do with HDD sizes greater then 137GB.

I dont understand why this >137GB issue is causing my boot failure.

Can anyone see what I am doing wrong with the creation of my RAID5 system?

I have run out of things to try and get this system up and work  please help

cheers
chipppy

---

