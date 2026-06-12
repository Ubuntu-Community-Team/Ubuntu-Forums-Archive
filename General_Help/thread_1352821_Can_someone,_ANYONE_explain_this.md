---
title: "Can someone, ANYONE explain this?"
date: 2009-12-12
forum: General Help
---

### Post by LAKOSWOLF on 2009-12-12
Greetings all,

Yes I've posted on this same topic before, (see [http://ubuntuforums.org/showthread.php?t=1305763]("http://ubuntuforums.org/showthread.php?t=1305763") ) but allow me to explain. After a massive crash which required me to reformat my hard drive I figured I'd give Karmic another try. To my surprise it went smoothly and I chalked it up to an update, bug fix or what have you.

All was going well until I plugged in my external HD, which failed to show up so I thought ok I'll reboot, and now I'm back to this drive mapper stuff again. (I have yet to get Ubuntu to see the external HD a MyBook) Now I'm seriously thinking about downgrading to Jaunty but for the life of me if anything I'd just like to know how or what this means!

[IMG]http://i64.photobucket.com/albums/h198/lakoswolf/windows.png[/IMG]

>The Blue window is the result of any attempt to get info with Gparted on Sdb or sdc.

> The orange window is the info window for /dev/mapper/pdc_caejidgdcg 

> The green window shows the drives as they show up in the pop-up menu of Gparted, Including /dev/mapper/pdc_caejidgdcg (149.05 GiB) which was cut off in the screenshot.

Further more I have attempted to mount both drives via CLI, my results:

> lakoswolf@GRAYWOLF:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a97aab8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29838   239673703+  83  Linux
/dev/sda2           29839       30401     4522297+   5  Extended
/dev/sda5           29839       30401     4522266   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbefcbef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe950e950

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux
lakoswolf@GRAYWOLF:~$ sudo mount -t ext3 /dev/sdb /media/stuff
mount: /dev/sdb already mounted or /media/stuff busy
lakoswolf@GRAYWOLF:~$ sudo mount -t ext3 /dev/sdc /media/stuff
mount: /dev/sdc already mounted or /media/stuff busy


Any information at all would be very useful!

Thanks!

---

### Post by bumanie on 2009-12-12
Suspect you need to a filesystem check on both the drives and see if that fixes any errors. Boot a live cd and try this is terminal > sudo e2fsck -C0 -p -f -v /dev/sdxxObviously you have to change the /dev/sdxx to you own drive designations and do this with the drives unmounted - you will have to do them separately. The code comes [from here]("http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem") if you want to check further details.

---

### Post by LAKOSWOLF on 2009-12-14
> **bumanie said:**
> Suspect you need to a filesystem check on both the drives and see if that fixes any errors. Boot a live cd and try this is terminal Obviously you have to change the /dev/sdxx to you own drive designations and do this with the drives unmounted - you will have to do them separately. The code comes [from here]("http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem") if you want to check further details.

Thank you for your reply! :)

I booted off a live Ubuntu CD and ran the command you posted above, it reported that there were errors (on SDC) and that the command would have to be run manually which I did. it also reported errors on SDC but not SDB.

Both drives mounted with the same name, which I found interesting given the fact that I've named them both differently. Only one of these drives was accessible, SDB.

In an effort to rule out distribution specific bugs, I booted off a Puppy Linux CD, both drives mounted and behaved normally, I was able to backup my data on the second hard drive that refused to mount under Ubuntu as well.

On a whim I decided to try a distribution upgrade from Jaunty rather than a fresh install, and for the moment it would seem this issue has resolved itself. (keeping my fingers crossed here).

Part of me wants to say this is a bug, but I can't say for certain. To be sure my drives are void of bad sectors I'm going to run DFT and see what the results are. I'll post them here.

[EDIT] I ran the tests on my hard drives and they all checked out as being fine.

I've also seen reports of the disk utility in Karmic reporting "Bad" sectors when there are none, which it has on SDB (the drive that I **could** access previously and none on the drive that was "bad" when I installed Karmic the first time)

---

