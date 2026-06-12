---
title: "Cannot change ownership of newly installed second hard drive"
date: 2010-01-06
forum: General Help
---

### Post by .Nate22 on 2010-01-06
Hey all-
I've been using ubuntu for a little while, but I still need help time to time. This post may seem long, but I'm trying to be as lucid as possible and describe what actions I have taken in a simple manner. 

Recently, I decided to wipe my system, put in two 250GB hard drives and rebuild my home file and print server. One of the hard drives is a SATA drive, and the other is not. In any event, they are identified as /dev/sda and /dev/sdb in Gparted. So far so good. 

Working on (reading from/writing to) the first hard drive (where the OS is installed) is no problem.  However, I have had difficulty trying to get my system to recognize my second hard drive and then allow me (nate) to read and write to said second drive. I followed these directions from the ubuntu community web page during installation:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

and setup my second hard drive with an ext3 file system. The drive is /dev/sdb. The PARTITION is /dev/sdb1. The MOUNT POINT is /media/TheBase250. 

The problem(s) begin at this point. I cannot:

1. Unmount the volume at my will-error says that only root can unmount

2. I am not sure if the command    sudo chown -R nate:nate /media/TheBase250  allowed me to take full ownership of said drive. It appears as if nothing changes when I run this command in terminal (even when I am root) Moreover, I cannot give myself permission to read and write files to the drive.

3. However, when I open up nautilus, browse to "TheBase250", right-click in the corresponding "explorer" or "finder" window and look at the properties for the drive, it says that "nate" is the owner (under the permissions tab), but again, I cannot give myself FILE read/write capabilities, nonetheless anyone else. When I try, all that happens is the corresponding box goes back to displaying "---"

4. Interestingly, if I skip nautilus and double-click on the drive from my desktop, again, logged in as nate (only user account created) and then proceed to right-click on the window that opens up, click properties, half the time it says that I cannot make changes to the permissions because I am not "nate." Well, last time I checked, I am nate, and this is, albeit delinquent, my computer. 

5. Another piece of information that may be helpful is that if I simply right-click on TheBase250 drive icon on my desktop itself, navigate to the permissions tab, the dialogue box says that "The permissions of "TheBase250" could not be determined"

Now, this is my cry for help, I hope you're moved enough to respond:

If you have any insight into this matter, please share your thoughts. Some additional information that may be helpful is the output from my fstab file. So, for your benefit, here is the output (the stars are not part of the file, but only to help improve readability):
*******************************************************
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9767f9b9-3c54-40ad-9475-dd12d2e7e1ad /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a289d25b-e0ac-4546-9d10-44a58c691ce7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /media/TheBase250   ext3    rw,suid,dev,exec,auto,user,async     0        2

******************************************************************
I should point out that I was having the same problems when I only had "defaults" instead of "rw,suid,dev,exec,auto,user,async" after the line with /dev/sdb1. I made the changes after reading this:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Again, thank-you for reading this. I hope you can help. 

Cheers,

Nate

---

### Post by doas777 on 2010-01-06
what filesystem is on the drive? is it actually ext3 as your fstab shows? 
I believe that the user that can unmount a drive is the one who mounted it, not the one that owns the files within it, or the folder to which it is mounted. since it is in fstab, that means that root is mounting it, so it stands to reason that only root could unmount it.  

hth

---

### Post by michy99 on 2010-01-06
It may be that there are errors on the drive, which would cause it to be mounted as read-only. Try running a fsck on the drive. (Unmount it first!)

---

### Post by Baelus on 2010-01-06
Can you post the output of

```
ls -ld /media/TheBase250
```

---

### Post by .Nate22 on 2010-01-08
Here you go. 
Running this:
root@uShotgun:~# ls -ld /media/TheBase250
Gives this:
drwxrwxrwx 3 nate nate 4096 2010-01-06 12:29 /media/TheBase250

Note: /media/TheBase250 is highlighted in green. I don't know if that means anything. 

Hope this helps to answer some questions my previous post raised. 

Cheers, 

Nate

---

### Post by .Nate22 on 2010-01-08
fsck came back clean. Here is what I did in terminal

root@uShotgun:~# fsck /dev/sdb1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
/dev/sdb1: clean, 11/15269888 files, 1006278/61049000 blocks

Any more thoughts?

---

### Post by .Nate22 on 2010-01-08
The drive is ext3. At least, that is how it is formatted in gparted.  Also, even if I do not resolve the mount-unmount issue, the larger problem is that I cannot create How do I change my settings so that the drive is automatically mounted at startup, and others can create folders, read and write files, and also delete files. I want all drives on my ubuntu computer to be completely open to everyone.

---

### Post by hwttdz on 2010-01-08
First back up your current fstab, I'd recommend backing up to the root partition, not home, that way if home doesn't mount for some reason you still have it.  

Second, how do you feel about uuid instead of /dev/sda (I don't even know the name for the latter, but uuid is more robust, and this seems like a good time to switch).  


pysdm is a graphical fstab editor with which I have a sort of love hate relationship.  It seems to be quite buggy in my experience, not liking comment lines in fstab.  It will allow you to check boxes for things like, everyone can write to this and whatnot.

---

### Post by bodhi.zazen on 2010-01-08
> **.Nate22 said:**
> Here you go. 
Running this:
root@uShotgun:~# ls -ld /media/TheBase250
Gives this:
drwxrwxrwx 3 nate nate 4096 2010-01-06 12:29 /media/TheBase250

Note: /media/TheBase250 is highlighted in green. I don't know if that means anything. 

Hope this helps to answer some questions my previous post raised. 

Cheers, 

Nate

That looks fine, what problem are you having ?

---

### Post by Morbius1 on 2010-01-08
Please post the output of the following command: **sudo blkid -c /dev/null**

---

### Post by Baelus on 2010-01-08
How about this:

As root, make a directory in TheBase250:

```
sudo mkdir /media/TheBase250/testdir
```

Change ownership:

```
sudo chown nate:nate /media/TheBase250/testdir
```

Then try writing to that directory:

```
touch /media/TheBase250/testdir/test.file
```

Do you still get a "Permission denied" error?

---

