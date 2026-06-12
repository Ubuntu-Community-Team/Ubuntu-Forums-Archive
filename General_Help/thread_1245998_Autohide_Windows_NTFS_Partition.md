---
title: "Autohide Windows NTFS Partition"
date: 2009-08-21
forum: General Help
---

### Post by t-vercetti on 2009-08-21
hey guys!

i've read many postings on this issue so far, but i don't seem to find an answer to my situation:

i want my ntfs windows partition to be invisible under "my places" or "computer" or wherever else it could appear. i do not want it unmounted, or no icon on the desktop: i want it invisible.
i wish i had the entry in fstab but i don't.
i run /etc/mtab and there i can see it when it's mounted.

here's the windows partition in my mtab:
/dev/sda1 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

and here's my fstab:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# / was on /dev/sda6 during installation
UUID=76ebda76-5d17-4d6f-b5af-8a8b980eb3ae  /              ext3         relatime,errors=remount-ro  0  1  
/dev/sda5                                  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0

further details:
my 80gb harddrive consists of the following partitions from left to right:
windows 15gb ntfs, swap 1gb, ext3 14gb, 50gb fat32

looks like my fstab only lists the ext3 and swap partition plus cdrom. where are the other 2 (ntfs and fat32)?

what i'd like to know is how i can make the windows partition disappear completely.
i followed a tip yesterday creating a mountpoint (sudo mkdir /mnt/sda1) and then adding the following line to fstab "/dev/sda1 /mnt/sda1 ntfs-3g defaults,locale=en_IN 0 0"

this worked fine as the partition was gone.
but somehow the 15gigs were added to the linux partition when i opened the gnome diskusage analyzer (babao) and also when i checked in "system monitor". it will tell me then that my linux system status is 30gb (the 15gb from ext3 and the 15gb from the hidden ntfs). i guess because it was mounted under the linux ext3 in order to make it disappear.

so how can i make it disappear without the mentioned side effect?

i found this wiki here but i don't know what to do with it, please help if this would solve my problem! 

[http://webapps.itcs.umich.edu/radmind/index.php/Hide_Windows_partition_in_dual_boot_setups](http://webapps.itcs.umich.edu/radmind/index.php/Hide_Windows_partition_in_dual_boot_setups)

thanx a lot,
greetz,
vercetti.

---

### Post by t-vercetti on 2009-08-21
ok, quick edit:

i ran "pysdm" and there i can see and configure my partitions. this is a gui for fstab. i came up with the following fstab file after hardly changing anything in pysdm:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                                       0  0  
# / was on /dev/sda6 during installation
UUID=76ebda76-5d17-4d6f-b5af-8a8b980eb3ae  /              ext3         relatime,errors=remount-ro                     0  1  
/dev/sda5                                  none           swap         sw                                             0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8                          0  0  

/dev/sda1                                  /media/sda1    ntfs         noexec,noauto,nosuid,nodev,noatime,nodiratime  0  0  
/dev/sda7                                  /media/sda7    vfat         users,noauto,user                              0  0  

now i just have to figure out how to make it invisible.
any tips?

thx,
vercetti.

---

### Post by mikewhatever on 2009-08-21
This worked for me-> [http://ubuntuforums.org/showthread.php?t=1060256](http://ubuntuforums.org/showthread.php?t=1060256).

---

### Post by t-vercetti on 2009-08-21
hey!

i found that answer just a couple minutes ago and tried it out myself.
rebooted and what do you know?! 
--> worked like a charm! :-)

i found your solution in these posts, just in case anyone needs them for reference:
[http://ubuntuforums.org/showpost.php?p=5696879&postcount=2](http://ubuntuforums.org/showpost.php?p=5696879&postcount=2)
[http://ubuntuforums.org/showpost.php?p=2605508&postcount=34](http://ubuntuforums.org/showpost.php?p=2605508&postcount=34)

so what's the problem here actually? why doesn't it work thru editing fstab?
and is this solution somehow doing anything "bad" or otherwise disadvantageously to the system, or is it ok to use this workaround?

thx + greetz,
vercetti.

---

### Post by t-vercetti on 2009-08-21
ok, the story continues:

in another forum i got a different  solution, this time without having to trick around with "hal".
it's just a plain and simple edit in fstab which is what i was looking for originally.

here's the line:
/dev/sdxx /mnt/sdxx ntfs defaults,umask=777,gid=46 0 0

(just make sure the right path is set, mine was /dev/sda1)

now i was wondering if it's possible to change the name "Filesystem" under my computer. setting the label with e2label won't change the appearance name. it will still be "Filesystem".

can this be changed? 

thx,
vercetti.

---

