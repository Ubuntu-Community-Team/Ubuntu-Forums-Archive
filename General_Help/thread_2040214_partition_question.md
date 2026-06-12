---
title: "partition question"
date: 2012-08-10
forum: General Help
---

### Post by Abbydabs on 2012-08-10
I'm trying to learn Linux partitioning and have a question.   I took my 36 gig SCSI drive and resized sda1 down to 18 gigs.   Then made an extended partition in the unallocated 18 gig space.   Then I created two 9 gig partitions in it.   I formatted them to ext4 like sda1.    When I tried using the partitions (creating a new folder) it says I don't have permission.    I thought I could cure that in file properties/permissions but I can't.  After playing around with it for some time I found that if I formatted those partitions to NTFS I could now use them to do whatever I wanted to do.  No problem with the "not having permission".    Did I do the right thing or  Is it better  to use ext2,3 or 4?   Thanks guys.

---

### Post by hgergo on 2012-08-10
In my opiniondepends: if you want to share whit windows the partition than leave ntfs when you use linux only than use ext4

---

### Post by Abbydabs on 2012-08-10
I have no plans on sharing with Windows but If I want to use ext 4 now I have to search or ask on how to get permission to use those partitions.  Will that create a problem by using NTFS in the Linux environment?   The partitions will be for storage only (pics, videos music etc.).   I like to keep my desktop clean so thus the storage partitions.

---

### Post by Wim Sturkenboom on 2012-08-10
How did you mount the ext4 partitions? Post the content of fstab or post the command that you used for mounting.

---

### Post by simonmoon42 on 2012-08-10
> **Abbydabs said:**
> I have no plans on sharing with Windows but If I want to use ext 4 now I have to search or ask on how to get permission to use those partitions.  Will that create a problem by using NTFS in the Linux environment?   The partitions will be for storage only (pics, videos music etc.).   I like to keep my desktop clean so thus the storage partitions.

Use the "chown" to change the owner to you. It is probably owned by root now.

```
sudo chown -R (user name) /dev/(device name)
```

Even if you do ext4 you can use Samba to set up sharing with Windows. It's a bit convoluted, but there are many guides to setting up Samba shares out on the interwebnets.

---

### Post by oldfred on 2012-08-10
If you keep it NTFS you need Windows to periodically or whenever you have issues run chkdsk. You cannot run chkdsk from Ubuntu. A Windows 7 repairCD will let you run the chkdsk if necessary. Ubuntu runs fsck after some many reboots to make sure file system is ok,

If NTFS you can only set ownership & permissions when you mount it. With Linux you can set ownership and permissions to suit your requirements.If a permanent drive it is best to mount with fstab and the settings you want.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

If ext4 and you want to manually mount a partition:
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#if not known to list partitions
sudo fdisk -l

I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 

To edit fstab:
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6

---

### Post by Abbydabs on 2012-08-11
Guys, I REALLY appreciate your help but learning this is sooooo hard for some reason.   I've been studying this for about a month now and am getting nowhere.  For example: I was asked how did I mount the ext4 partitions and to post the results of fstab.   I don't know how to answer those questions.  I installed Lubuntu but I never was asked where to mount anything during the install.   Then with fstab I had to google it as that is also new to me.  I read about fstab then tried to open it in terminal with "/etc/fstab" like it said to do but I get a  "command not found" error message.  Then I tried the suggested "sudo chown -R" using my name and dev name but again ...errors.   Frustration sets in.   I turn off the computer and think about giving up.   But, later, I'm back googleing and reading but it doesn't help.   I don't know how you guys do it but my hat is off to you.  It's as easy as breathing to you but for me it's like learning Chinese.  I don't know if there is a "Linux for Dummies" book but I'm going to take a trip to the mall and find out.   So there is no need for any more replies as I'm going to take a break from this for a while as it's taking up most of my time.  Thanks guys.

---

### Post by Mr. Beekeeper on 2012-08-11
DON'T GIVE UP : )

I can speak newbie to you, because I still am one. 

Fstab is where Linux looks to see what drives it will automatically  mount.  The reason why you weren't able to see it is because you weren't  telling it what program to use to read it.  Nano is the default editor  for Ubuntu, and the one I use.  You can use it by typing:


```
nano /path/to/whatever you're going to.txt
```

Try cutting and pasting this into a terminal:

```
nano /etc/fstab
```

Note!  to exit nano, hold the control key and hit x.  The ^X, ^G, ^etc at the bottom of the nano screen means "hold ctrl and the key for this function".  Your mouse pointer is pretty useless in nano except for copying.  You have to use the arrow keys to navigate.

Learning to use a text editor will get you really far in working with Linux, don't fear the command line, you'll learn to love it eventually.  I hope this helps!

---

### Post by Mr. Beekeeper on 2012-08-11
Also, you might listen to the Linux Reality Podcast...


Especially this episode, it explains how the Linux Filesystem works:

[http://archive.org/details/lrp011](http://archive.org/details/lrp011)

---

### Post by Abbydabs on 2012-08-12
Mr. Beekeeper, Thanks for your encouragement  AND understanding on not giving up.   I did some more reading today on how to gain ownership of a partition and found a nice site that explained it  pretty clearly.  It was similar to what simonmoon42 suggested but a colon was used between user and group name.   Plus, I was using the partition name (sda3) for the device name.  When I changed it to "/media/ad163e1d-1b0f-4741-876e-830dfe184695" that appears in file manager ...IT WORKED!!!   I can now used the partition to read and write to.  I am going to checkout the  Linux Reality Podcast... you have suggested.    The "nano /etc/fstab" you said to use also worked.  Why didn't the site I went to list that?   They didn't list the "nano" just the etc/fstab.   That's why it didn't work for me.  Thank you sooooo much for your help and the rest of the guys too.   I'm learning.......and am enjoying it.

---

### Post by Mr. Beekeeper on 2012-08-12
Glad you didn't get discouraged!  I wish someone would have explained basic command line stuff to me when I was new to Linux.  (I should have asked!).  

Here's a few command line gems:

```
man program-name
```

Where "program_name" is the name of the program that you want to learn about will open up the manual page for that program..it'll tell you loads of info.  

Most command line programs work in this format:

```
program_name -a -b -c 
```

Where "program_name" is the name of the program you want to use and the "-a -b-c" are options.  The options will be listed in the "man" manual pages.  You can also type :

```
program_name  --help
```

For a shorter list of options than the "man" page.  

Knowing how to use the "man" page for programs and how to edit text files (via nano) will get you really far in Linux.

Cheers!

---

