---
title: "Moving /tmp and /var to another partition (after install)"
date: 2011-06-12
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-12
i am going to be upgrading to a ssd and would like to move [FONT=Courier New]/var[/FONT] and [FONT=Courier New]/tmp[/FONT] to a separate partition (it can be separate but preferably the same)
how would i extract [FONT=Courier New]/var[/FONT] and [FONT=Courier New]/tmp[/FONT] to a different partition (need fstab lines and permission settings)
when i get another stick of ram i will make [FONT=Courier New]/tmp[/FONT] into a ram disk
here is my partition layout
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=194908&stc=1&d=1307882235[/IMG]

---

### Post by prodigy_ on 2011-06-12
Chroot from a LiveCD into your installation. Edit /etc/fstab. 

Then pack /var (assuming bash): ```
cd /var
shopt -s dotglob
tar -cvjf var.tar.bz2 *
```
Unpack the archive to the partition you're going to mount as /var. Then delete everything in /var and reboot.

You can use something else instead of tar, for example **find . -depth -print0 | cpio --null -pvd <destination>**. But tar is probably the easiest.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
```
tmpfs /tmp tmpfs nosuid,nodev 0 0
```when i switch /tmp to a ram disk in the future that will be the new fstab line right (that i copied from the live cd)?
assuming the new 2gb partition's uuid is decf38bf-6b4d-4acc-90db-0f18760310f5
if anyone cares that id is off a old install i have on another hdd
current fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=31291866-5557-4805-b357-b504685e2cf7 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=6b36b3b7-731a-4372-be35-9f25016f58b9 none            swap    sw              0       0
# ram disk
tmpfs /home/chad/Desktop tmpfs size=60M,nr_inodes=10k,mode=777 0 0
tmpfs /home/chad/.mozilla/firefox/main.default/Cache tmpfs size=65M,nr_inodes=10k,mode=777 0 0
```if there is a issue in my last 2 lines let me know i do not understand the last 3 parts of a fstab line ([FONT=Courier New]defaults 0 2[/FONT] for example)
edit:
i figured out the fstab liens i will need
[https://help.ubuntu.com/community/MoveMountpointHowto](https://help.ubuntu.com/community/MoveMountpointHowto)

---

### Post by pqwoerituytrueiwoq on 2011-06-13
it is failing some sanity check something involving a gconf thing in the /lib folder
exiting status is 256
edit:
[http://ubuntuforums.org/showthread.php?t=1781734](http://ubuntuforums.org/showthread.php?t=1781734)

---

### Post by MeduZa on 2012-01-22
I used bind on fstab to do the same:
```
/home/jail/var /var bind defaults,bind,noatime,mode=0755 0 0
/home/jail/tmp /tmp bind defaults,bind,noatime,mode=1777 0 0
```

but you can move it to ram if you have tons of it:

```

tmpfs	/tmp		tmpfs defaults,noatime,mode=1777 0 3
tmpfs	/var/tmp	tmpfs defaults,noatime,mode=1777 0 3
tmpfs	/var/log	tmpfs defaults,noatime,mode=0755 0 3 
tmpfs	/var/log/apt	tmpfs defaults,noatime 0 3

```
(the contents will be destroyed on reboot)

remember to set noatime, nodiratime, discard on the ssd disk
also remember to disable the elevator on the SSD (he don't need that is an flash disk and elevator is for rotary disk)

---

