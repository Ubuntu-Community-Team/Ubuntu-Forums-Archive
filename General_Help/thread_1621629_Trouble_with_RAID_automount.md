---
title: "Trouble with RAID automount"
date: 2010-11-14
forum: General Help
---

### Post by squids on 2010-11-14
Hi, I'm a completely new user to Ubuntu and am trying to set it up on my home media server. I've had a varety of problems while trying to get ubuntu to act as a file server to connect to windows 7 machines and have spent alot of time fixing them but now have one problem I can't seem to solve with hours of googling.

I have 3 2tb drives that I raided into one huge drive. To do this i had to install something called mdadm as it wasn't installed by default. Everything seemed to work but then I found whenever I restarted I had to remount the array and put in a password to access it. 

I googled and there was an ubuntu help page saying use something called pysdm. After installing that, I had a look, couldn't see anything about automounting but ticked one textbox that said allow all users access to this drive. That was a mistake, ubuntu wouldn't boot after that and I had to take the case apart and plug in a cd drive to run the live cd so I could edit my fstab file.

So after spending a couple hours working out how to do that I googled some more and found threads on this board on how to edit your fstab file and mdadm.conf to allow the raid to automount on boot. None of the combinations suggested worked so I tried someone's suggestion of reinstalling mdadm as it would automatically detect the raid and fill in the correct line. Another mistake there, now my raid array says "Not running, partially assembled" and that's where I'm stuck now.

That is, aside from not being able to get samba to start on boot as it it doesn't seem to be anything in the init.d directory to start the service

Here is my fstab file

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c03d134d-af43-4f69-b7a2-59c6e2e1cd4c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID="ea0a4bb5-bcae-4e10-9607-d7c0af01ffb1 /media/Array ext4 defaults 0 2

Here is my mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/Array level=raid5 metadata=1.2 num-devices=3 UUID=8b222fa8:a8fb1461:ef12462c:f225f8d2 name=:Array

# This file was auto-generated on Sun, 07 Nov 2010 22:01:12 +0000
# by mkconf $Id$

Anyone have a clue what's wrong?

---

### Post by sohlinux on 2010-11-14
sounds like a complicated way of going about it. if the drives are empty it may be easier to start from scratch by using the disk utility to create the raid array and use mountmanager to sort out your fstab  and samba mounts.

---

### Post by squids on 2010-11-14
Hi, Mountmanager looks promising, thanks, but I can't see my raid array, just it's individual disks, could this be because disk utility says it's "Partially assembled not running". Any idea how to get it running again without 12 hrs of array rebuilding?

---

### Post by sohlinux on 2010-11-14
yep mountmanager is not reading them as raid

backup your mdadm.conf open it with gedit then change the following line 

from: DEVICE partitions to: DEVICE UUID="ea0a4bb5-bcae-4e10-9607-d7c0af01ffb1 /media/Array

---

### Post by squids on 2010-11-14
Changed that line but it still says raid is partially assembled

---

### Post by sohlinux on 2010-11-14
> **squids said:**
> Changed that line but it still says raid is partially assembled


did you keep a backup of your original mdadm.conf file? if so can you paste it here?

if not then maybe its easier to rebuild the array or simply don't use raid.

---

### Post by squids on 2010-11-14
I don't have my mdadm from before the madam uninstall, only the file in my opening post

---

### Post by sohlinux on 2010-11-14
in ect/fstab change the following line for the red line below [COLOR="Red"]UUID="ea0a4bb5-bcae-4e10-9607-d7c0af01ffb1 /media/Array ext4 defaults 0 2[/COLOR]



proc /proc proc nodev,noexec,nosuid 0 0

/dev/sdb1 / ext4 errors=remount-ro 0 1

UUID=c03d134d-af43-4f69-b7a2-59c6e2e1cd4c none swap sw 0 0

/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

[COLOR="Red"]UUID=8b222fa8:a8fb1461:ef12462c:f225f8d2 /media/Array ext4 defaults 0 2[/COLOR]

---

### Post by squids on 2010-11-14
no joy after changing that im afraid, still says array not running

---

### Post by sohlinux on 2010-11-14
> **squids said:**
> no joy after changing that im afraid, still says array not running

it very likely would have worked if you had you original mdadm.conf

if the raid is still partially assembled you may have to rebuild the array unless someone else here has an idea.

---

### Post by squids on 2010-11-14
Many thanks for your help,  it doesn;t look like there's much hope of fixing it so I've tried to rebuild the array but it wouldn't. I then clicked 'tear down array' and it did but now I can't see what I can do from here. The only option is "start raid array" and that gives an error "One or more block devices are holding /dev/sdc1"

Any idea what might be going on?

---

### Post by sohlinux on 2010-11-14
you need to clear your fstab so you only have the bootable partitions active and your swap active then format the other drives and use the disk utility to create the raid array again.

backup everything first

---

### Post by squids on 2010-11-16
Hi, I've managed to format 2 of the partitions and change my fstab but disk utility wont let me format the third saying "The device is busy. One or more partitions are busy on /dev/sdc

---

### Post by sohlinux on 2010-11-16
> **squids said:**
> Hi, I've managed to format 2 of the partitions and change my fstab but disk utility wont let me format the third saying "The device is busy. One or more partitions are busy on /dev/sdc

you need to do it with the live cd so you can unmount all the drives in question

---

### Post by squids on 2010-12-13
Hi, I don;t know if you're still about as it's been a long time since I last posted but I have more errors I'm afriad.

I unmounted then tore down the array, rebuilt it, partitioned and It said "warning this partition is misaligned by 506880 bytes. This may result in very poor performance, repartition is suggested"

So I tore it down again and rebuilt and it still says that, any ideas?

Would it be easier for me to buy a hardware RAID card or two for christmas? Would they be easier to manage? I'm concerned as I've had to tear down the array three times now, if it had any data on it it would be catastrophic. Can you actually recover the data on a software raid?

Thanks in advance

---

### Post by sohlinux on 2010-12-13
you could try a RAID card but personally I wouldn't even bother using raid, you can just make a backup onto some other drives. 

you can recover data from a raid failure but sometimes it can be very difficult with misaligned raid partitions. if your data is very important then you should backup on a remote server or just store a backup on some removable drives.

---

### Post by squids on 2010-12-13
Maybe you're right, I'm so fed up with RAID and the whole process. My main concern though is that 6tb of data is going to be very difficult to backup

---

### Post by sohlinux on 2010-12-13
> **squids said:**
> Maybe you're right, I'm so fed up with RAID and the whole process. My main concern though is that 6tb of data is going to be very difficult to backup

yes raid can be troublesome and its not always 100% guaranteed that you can recover all your data if one of the drives fails, now 2tb external drives are very cheep, just seen them on ebay for 60 GBP each, its a cheep way to backup large amounts of data at home but if you need to backup remotely get a cheep dedicated server and get them to add 3 x 2tb drives.

---

### Post by barjammar on 2010-12-23
Hi,
I am having the same problem.  I have four 2TB SATA drives on sd[a-d] which is giving errors in the disk utility ( palimpsest ).  I can't start the RAID at present because "one or more block devices are holding dev/sdb" and I see various new block devices for some reason.  A link to the screenshot is below.

[IMG][https://photos-1.dropbox.com/i/l/pyBmQRqcN-iDEmZiSfIOC-lxmzasnos7XmZ1ihi57Oc/6252029/1293242400/5c022e3#1](https://photos-1.dropbox.com/i/l/pyBmQRqcN-iDEmZiSfIOC-lxmzasnos7XmZ1ihi57Oc/6252029/1293242400/5c022e3#1)[/IMG]

Like you, I am attracted to the concept of having one massive drive.  If I can get this working safely then I won't have to worry about it for several years.  I have an old system with RAID5 and it has served me well, but is only 2TB.

THE GOOD NEWS IS: My son-in-law ( TB ) fixed it for me yesterday - so when he re-fixes it I will post the fix steps.  Right now I will re-start the machine and see if it reconstructs the raid from fstab listings.  I think this problem happened because I restarted the machine the "skipped" the reconstruction and mounting of the RAID 5 when Ubuntu re-booted.  Maybe it then made a few "block devices".
;)

---

### Post by barjammar on 2010-12-24
From Troy Bebee

Our symptoms were that our mdadm RAID was running fine until a reboot. After a reboot the RAID array could not be started because the several of the member drives were already configured in a /dev/dm-0 raid set. The problem was that the dmraid configuration was grabbing some of the disks at boot and trying to activate them as RAID devices. Since we setup our RAID through mdadm we don't really want dmraid messing about with our RAID sets. To fix this you can check for dmraid configuration and remove it as follows:

> dmsetup info
> dmsetup ls
> dmraid -s

If you have configuration under dmsetup which you do not want you will first need to remove the drives from dmraid and then remove the configuration metadata. Run the following:

> dmsetup remove <device>
> dmraid -x <configuration>
> dmraid -s

Once the devices are released from dmraid you will be able to startup your mdadm array.

> mdadm --assemble /dev/md0

Note from Barjammar: I'll update this and post a log file if I get time.
:D

---

