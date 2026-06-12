---
title: "cannot change current block/inode  allocation"
date: 2010-02-08
forum: General Help
---

### Post by sulekha on 2010-02-08
Hi all,

I was trying to unable quota s on my ubuntu jaunty system, but i am getting this error

sudo edquota -u testuser
edquota: WARNING - /dev/sdb5: cannot change current block allocation
edquota: WARNING - /dev/sdb5: cannot change current inode allocation

contents of my /etc/fstab file are as follows:-

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=985f9223-4d26-40ab-979f-1804a0b65634 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7f5a8931-c8f8-4462-9169-5375b55c3868 none            swap    sw              0       0

/dev/sdb5       /data           ext3 relatime,usrquota,grpquota  0 1      
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

these are the steps followed by me :- 

 sudo apt-get install quota
 sudo mount -o remount /data
 sudo quotacheck -cugm /data
 sudo quotaon -augv

---

### Post by tacom6 on 2010-06-09
I am having a similar problem.... must get this to work.

---

### Post by jringoot on 2012-02-08
Are you sure quota is on? 
This behaviour is typical when quota is off.
What is the output of:
[FONT="Courier New"] quotaon -avugp
[/FONT]

It should show that quotas are on, if not try:
 [FONT="Courier New"]quotaon -avug
[/FONT]
and retry the edquota.

---

