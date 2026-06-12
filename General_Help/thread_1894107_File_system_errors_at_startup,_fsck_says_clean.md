---
title: "File system errors at startup, fsck says clean"
date: 2011-12-11
forum: General Help
---

### Post by wannabegeek on 2011-12-11
Hi all,

When I boot up, during the disk check operation, I have gotten three failures to mount
some ext4 partitions. There partitions are not root and have no OS, just music and stuff.

When I check in a terminal with fsck, the program says the partitions are clean.

It appears there is nothing wrong with any of my volumes and they all end up mounted after the failure is reported.

I have updated my kernel lately and added an SSD drive and new fstab.
I didn't have this problem before, it just came up today.

Google didn't turn up any obvious answers so I wanted to post here while I continue to look. There are some older forums posts but none are solved.

thanks in advance,
wbg

---

### Post by jerrrys on 2011-12-13
I too use non-boot ext4 partitions and at times an executable file or .iso will attempt to boot if stored in the top level of these partitions.

---

### Post by wannabegeek on 2011-12-14
> **jerrrys said:**
> I too use non-boot ext4 partitions and at times an executable file or .iso will attempt to boot if stored in the top level of these partitions.


Is that what happens...? I don't think I have any executables or iso's on the volumes being 
flagged....

thanks for the idea though, I'll look into it.

wbg

---

### Post by mcduck on 2011-12-14
Could you run "sudo fdisk -l" and "blkid" & post the outputs here together with your /etc/fstab file?

---

### Post by wannabegeek on 2011-12-15
Hi Mcduck...

Here's my fstab, NOTE, I did remove the boot time check from it.
blkid output is below it.

I forgot an important change I made before this whole problem started. I did not get the volume warnings until after I installed a new SSD ( sdb ) and put installed Ubuntu on it.

I also recently added my Old Root and home to my fstab, but the warnings occured before they are added.
 

thanks !


[PHP]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c2d8a3d6-66f7-4d72-9009-2a7da9d00cc2 /               ext4    discard,errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=c14e2b20-950b-4327-a9c5-2cb48d066e26 /home           ext4    discard,defaults        0       2
# /media/Music was on /dev/sda9 during installation      
UUID=d5c5d254-6614-45b3-a6e4-8664f55649b6 /media/Music    ext4    defaults        0       0
# /media/Pics was on /dev/sda10 during installation
UUID=34f9d66e-5502-4e1a-aefe-1732b81ce9a2 /media/Pics     ext4    defaults        0       0
# /media/Video was on /dev/sda8 during installation
UUID=915a523c-e2f1-49ae-9864-b3bdd78646de /media/Video    ext4    defaults        0       0
# /mnt/Data was on /dev/sda11 during installation
UUID=02244003-530d-467f-a425-cee4ba1a9a02 /mnt/Data       ext4    defaults        0       0
# mount old ROOT filesystem for things like matlab
LABEL=Old_Root                            /mnt/old_root   ext4    defaults        0       0
# mount old HOME
LABEL=Old_home                            /mnt/old_home   ext4  defaults          0       0
[/PHP]


[PHP]
/dev/sda5: LABEL="Swap" UUID="5fa4afa7-eb79-46bc-9675-693036e54756" TYPE="swap" 
/dev/sda6: LABEL="Old_Root" UUID="fa9c5d36-26b0-4020-88b5-fb4906b871fd" TYPE="ext4" 
/dev/sda7: LABEL="Old_home" UUID="7f7ebff2-98e1-40f6-8674-af2f05e0000d" TYPE="ext4" 
/dev/sda8: LABEL="Video" UUID="915a523c-e2f1-49ae-9864-b3bdd78646de" TYPE="ext4" 
/dev/sda9: LABEL="Music" UUID="d5c5d254-6614-45b3-a6e4-8664f55649b6" TYPE="ext4" 
/dev/sda10: LABEL="Pics" UUID="34f9d66e-5502-4e1a-aefe-1732b81ce9a2" TYPE="ext4" 
/dev/sda11: LABEL="Data" UUID="02244003-530d-467f-a425-cee4ba1a9a02" TYPE="ext4" 
/dev/sdb1: LABEL="SSD_ROOT" UUID="c2d8a3d6-66f7-4d72-9009-2a7da9d00cc2" TYPE="ext4" 
/dev/sdb2: LABEL="SSD_HOME" UUID="c14e2b20-950b-4327-a9c5-2cb48d066e26" TYPE="ext4" 


[/PHP]

---

