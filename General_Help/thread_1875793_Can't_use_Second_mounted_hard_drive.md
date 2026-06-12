---
title: "Can't use Second mounted hard drive"
date: 2011-11-05
forum: General Help
---

### Post by cherryredz on 2011-11-05
Hi, did a fresh install on my system 11.10 all went well.
Got 2 hard disc both sata one 250G the other 120G.
plan was to use smaller one to save back-ups and store pictures and music files.

Both discs got ext4 file system the small disc mounts on boot up but I cant create folders (option is "greyed out") or move any files to it (by cut and paste or attempting to save file directly to it), if I try to open the "lost&found" folder in it I get the following message: 

You do not have the permissions necessary to view the contents of "lost+found".

Does anyone have an idiots guide as to what I need to do to be able to use/access this disk.

many thanks ....cherryredz

---

### Post by hwttdz on 2011-11-05
You don't have permissions because root owns the drive.  

You need to give other users permissions as root. (by which I mean use root to give permissions on the drive, not give user root permissions, the second would be bad)

Look at the output of 
ls -l /path/to/mount

it will probably read something along the lines of

drwx------- root root .....

which means that root can read,write,execute (rwx), group can do nothing (first ---), other can do nothing (---) and there's one extra which sometimes holds extra information.  

I'm not sure what permissions you want, so unless you tell us who you want to be able to do what we can't help so much.  And in general lost and found is owned by root and does not allow any users to look in it.

---

### Post by oldfred on 2011-11-05
Some links to more info.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Manually mounting it.
sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone, if multiuser you may not want everyone to have access.
I just learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

---

### Post by cherryredz on 2011-11-06
Thanks for the replies, normally go into panic/worried mode when faced with command line instructions/solutions but I'm persevering.

One of the links from Oldfred hit the nail on the head for what I was looking for.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Followed it from start to finish and it worked a treat, my 2nd hard drive is now automatically mounted on start up (it wasn't before only seen by the system and able to be manually mounted) and I can save to, copy to and delete from with no problems.

Appreciate you guys taking the time to reply to my question, thank you

.............cherryredz

---

