---
title: "automatically mount partitions at boot"
date: 2011-07-02
forum: General Help
---

### Post by mrchumpley on 2011-07-02
I have been using Ubuntu for a couple of years and now use 10.04. I think it's brilliant even though I'm not very good doing stuff in terminal.

I have two sata drives. The first has /, swap and a partition Label "Database". The second has three partitions labeled "Video", "Photos" and "Documents". All the labeled partitions are ext3.

Currently I have to mount the labeled partitions manually after booting up. What I've wanted to do for ages, and tried to do some time ago but gave up, is have them mount automatically when I boot up.

I have tried editing fstab according to a post I saw about automatically mounting NFTS partitions, but it didn't work (it nearly did, I think).

This is what I get when I run the following commands in terminal:

nevil@Ubuntu1:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/nevil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nevil)
/dev/sdc1 on /media/WD Passport type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda2 on /media/DataBase type ext3 (rw,nosuid,nodev,uhelper=udisks)

nevil@Ubuntu1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6149e2dd-4bad-4984-a967-a891e15cfac6 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=94e9f234-0c46-4380-8d56-90d768386602 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

nevil@Ubuntu1:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="6149e2dd-4bad-4984-a967-a891e15cfac6" TYPE="ext3" 
/dev/sda2: LABEL="DataBase" UUID="76df9e85-3238-4da7-959b-e217524bc37d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="94e9f234-0c46-4380-8d56-90d768386602" TYPE="swap" 
/dev/sdb1: LABEL="Video" UUID="639e9e60-8c6b-4d37-8a9e-45ea01c60416" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: LABEL="Photos" UUID="91459d49-4974-4e61-bcbe-9876a673d780" TYPE="ext3" 
/dev/sdb3: LABEL="Documents" UUID="b4b6c5ca-64db-47ea-afbd-1098e4889a8e" TYPE="ext3" 
/dev/sdc1: LABEL="WD Passport" UUID="692B-6507" TYPE="vfat" 
nevil@Ubuntu1:~$ 

I assume I need to edit fstab with the UUIDs of the partitions and instructions to mount automatically? Could someone tell me how to do this?

Many thanks
Nevil

---

### Post by Morbius1 on 2011-07-02
[1] Make permanent mount points for these partitions:
```
sudo mkdir /media/DataBase 
sudo mkdir /media/Video
sudo mkdir /media/Photos
sudo mkdir /media/Documents
```[2] Add the following lines to the end of /etc/fstab:
```
LABEL=DataBase /media/DataBase ext3 defaults,noatime 0 2
LABEL=Video /media/Video ext3 defaults,noatime 0 2
LABEL=Photos /media/Photos ext3 defaults,noatime 0 2
LABEL=Documents /media/Documents ext3 defaults,noatime 0 2
```[3] Save fstab and in a terminal run the following command that will test for errors and mount the new partitions:
```
sudo mount -a
```If it comes back with errors post them. If it comes back to the prompt it ran successfully. See if the mount points have the data you expect.

---

### Post by oldfred on 2011-07-02
I rely on Morbius1 for good understanding of mounting, permissions & ownership issues. And regularly refer to his previous posts.

But I think he has a typo on defaults in each of these lines:

LABEL=DataBase /media/DataBase ext3 [COLOR=Red]defualts[/COLOR],noatime 0 2

---

### Post by Morbius1 on 2011-07-02
You are correct :oops:. Not only once but 4 times!

Thank ( fill in the name of your personal deity ) for peer review.

---

### Post by mrchumpley on 2011-07-02
Amazing.

Thank you so much!

I have another issue that has been annoying me for more than a year, but it's not relevant to the title of this thread so I guess I should start a new one. (It's to do with permissions and accessing stuff on the partitions that I am unable to see.) 

I will have another search of the forums and post a new thread if I can't figure it out.

Thank you again for your help. I'm so pleased!

Nevil
:D

---

### Post by oldfred on 2011-07-02
Do not include the -r recursion unless you are absolutely sure you are in a data only partition. I made that mistake (only once) and had to reinstall as root has to own most system files & folders.

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
sudo chmod -R 777 /data
sudo chown -R $USER:$USER /data
#where $USER should be your login name
#or to see user
echo $USER


More info:
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by mrchumpley on 2011-07-04
Thanks Oldfred - that is helpful.
n

---

### Post by Morbius1 on 2011-07-04
In an attempt to redeem myself from my earlier mistake I would like to point out that the following command is not necessarily a good idea:
>  sudo chmod -R 777 /dataIt will make every subdirectory executable which is what you need in order to open it to see what's inside. But it will also make every file executable as well.

An alternate way that works around this problem is to use something like this:
```
sudo chmod -R a+rwX /data
```All subdirectories will be marked rwx for user, group, and others. The big "X" will also not make files executable unless they were executable to begin with. There is no way to reproduce this using octal notation.

Just an FYI.

---

### Post by mrchumpley on 2011-07-05
I am a little be confused now!

These later comments seem to be about accessing data on partitions that I couldn't see but suspected was there, rather than being about automatically mounting the partitions? I did start a separate thread about this - should these comments belong to that thread?

n

---

### Post by Morbius1 on 2011-07-05
Actually the "chmod -R 777" vs " chmod -R a+rwX" discussion is totally off subject. My comment was a knee jerk reaction to seeing a recursive chmod 777 and it's undesired consequences. 

Sorry about that.

---

### Post by mrchumpley on 2011-07-05
:lol:

n

---

### Post by dcstar on 2011-07-05
> **mrchumpley said:**
> I am a little be confused now!

These later comments seem to be about accessing data on partitions that I couldn't see but suspected was there, rather than being about automatically mounting the partitions? I did start a separate thread about this - should these comments belong to that thread?

n

And for all the mucking around with the fstab file in this thread you could have simply installed the **pysdm** package and used that GUI to set up the automatic mounting of the partitions.

---

### Post by Morbius1 on 2011-07-05
Mucking about ? :lol:

Seriously though, the last time I checked, Pysdm is incapable of mounting a device by LABEL or even UUID so your comment is a bit of a non-sequitur. The higher the number of partitions the greater the need to mount by the default UUID demarcation as the Ubuntu installer uses or LABEL's.

---

