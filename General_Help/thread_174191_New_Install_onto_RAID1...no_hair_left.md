---
title: "New Install onto RAID1...no hair left"
date: 2006-05-11
forum: General Help
---

### Post by Pelham123 on 2006-05-11
Please can someone put me out of my misery....

I have an NForce4 MOBO with two blank samsung 80gb HDD. I am trying to set up a RAID1 (because I want to :p ) but am having trouble at he re-boot stage of the install. System hangs after BIOS (just before the GRUB stage). 

What has confused me was the partitioning section of the install, this is how I did it...

1) Allow the full space of the two disks to be allocated to software RAID
2) Created a new MDD under the software RAID (MD_0)
3) Partitioned the RAID into / & swap
4) As it is a mirror set-up, selected  two partitions to be active, the other two in-active
5) Installed 

What has confused me is the bootable flag options, - does only the active partition need to be flagged? 

Really would like some help, I have tried quite a few different partition choices but to no avail. 

My hair is going, please help before I have to invest in a rug....

---

### Post by lha on 2006-05-12
[QUOTE=Pelham123]
1) Allow the full space of the two disks to be allocated to software RAID
2) Created a new MDD under the software RAID (MD_0)
3) Partitioned the RAID into / & swap
4) As it is a mirror set-up, selected  two partitions to be active, the other two in-active
5) Installed 

What has confused me is the bootable flag options, - does only the active partition need to be flagged? [/QUOTE]

Did you really create only one md device and then created two partitions *inside* it? AFAIK, you should use md devices a bit like partitions. Like create identical partitions (hda1~hdc1 and hda2~hdc2) on both drives, marking them both all raid. Then create md devices md0 from hda1 and hdc1, md1 from hda2 and hdc2. Then use md0 for root and md1 for swap.

Don't worry about bootable-flags. If you have grub on mbr, they don't have any meaning for you.

---

### Post by Pelham123 on 2006-05-12
Ahh..ok.

Will give it a go and edit this later with the results. Thanks! :)

---

### Post by Pelham123 on 2006-05-12
Right, this is what happened....

1) Made matching primary partitions on both HDDs and set the 'use as' Software RAID
2) Write changes
3) Created MD_0 and MD_1 by choosing the matching /dev/ | /lun0.... per MDD and made 1 active and 1 spare per partition.
4) In the partition table I now have 2 MDDs; these were assigned as ext3 mount point '/' and swap area.
5) Write changes to disk
6) Install goes as per normal, get to the eject CD and re-boot
7) Boots past BIOS into... 

'Loading GRUB stage 1.5

GRUB Loading, please wait.......'

System hangs.

I have got Ubuntu dual booted onto a single HDD with XP. Can I use this to look at the GRUB? I have tried the rescue disk, but it says there isn't a valid mount point, I can get a shell, but with a very limited command line.

Any ideas gratefully received ](*,)

---

### Post by lha on 2006-05-12
> **Pelham123]Right, this is what happened....

1) Made matching primary partitions on both HDDs and set the 'use as' Software RAID
2) Write changes
3) Created MD_0 and MD_1 by choosing the matching /dev/ | /lun0.... per MDD and made 1 active and 1 spare per partition.
4) In the partition table I now have 2 MDDs said:**
> (*,)

First, you want to make both partitions in a md device active. If you had three drives and made two partitions active and one spare, in case of hd failure the spare drive would replace the failed drive and mdadm would immediately begin to mirror data from working active drive to the spare drive. Spare drive would then become an active drive. As you have only two drives, making the other a spare drive does make much sense.

It may be possible to mount md devices in your working Ubuntu. I've got Dapper running on a single drive, but I can mount my raided Breezy drives like they were normal partitions. Dapper's mdadm starts md devices automatically and I didn't configure anything to make it do so. I just use 'sudo mount -o ro /dev/md1 /mnt/' to mount md1 to /mnt as read-only.

Those booting problems sound strange. Are you using pata or sata drives? What device names each of your drive has? What booting order you have in bios? How do you select between Ubuntu/Windows or would-be-new-Ubuntu when you boot?

---

### Post by lha on 2006-05-12
I just found [this page]("http://www.miquels.cistron.nl/raid/") which is about creating partitionable raid1 devices. So it seems I was wrong when I told that this isn't possible. But it sure does look more complicated than making non-partitionable md devices.

---

### Post by lha on 2006-05-12
I just found [this page]("http://www.miquels.cistron.nl/raid/") which is about creating partitionable raid1 devices. So it seems I was wrong when I told that this isn't possible. But it sure does look more complicated than making non-partitionable md devices.

---

### Post by Pelham123 on 2006-05-12
Success!!

Firstly, thank you very much for all your time and effort :KS 

They active partition step seemed to be the problem. My logic was, that if it was a mirror, then only one would need to be active - the other (spare) would also have data written to it, but only used if the other failed...

So, am now writing this forum entry with 5.10 on a RAID1 - yay!

Although I must confess to being suspicious - but I SPM'd Gparted and it showed a RAID config!

Done! :-D 

Thanks again

---

### Post by lha on 2006-05-12
Nice to hear you made it!

A better way to check you are on raid is to look at /proc/mdstat. Run 'cat /proc/mdstat' and you should see something like

Personalities : [raid1]

md1 : active raid1 hda1[0] hdc1[1]
      9254780 blocks [2/2] [UU]

md0 : active raid1 hda2[0] hdc2[1]
      571672 blocks [2/2] [UU]

unused devices: <none>

Also, 'df -h' shows how much free space you have on each filesystem and some other info, too.

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              9.1G  4.9G  4.2G  52% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile

Main interest here is that md0 is used as root.

Remember, if you want to keep your system bootable even if your drive with grub suffered a failure, you have to manually install grub to the other drive.

---

### Post by Pelham123 on 2006-05-12
Proof is in the pudding (or screenshot in this case)

andy@ubuntu:~$ cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 sda5[0] sdb5[1]
      2931712 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      29294400 blocks [2/2] [UU]

unused devices: <none>
andy@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               28G  2.1G   25G   8% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile

Taa-daa!

Thanks to you ;) 

ps - will bear in mind about the GRUB and drive fail, hopefully wont have to post about that...

---

