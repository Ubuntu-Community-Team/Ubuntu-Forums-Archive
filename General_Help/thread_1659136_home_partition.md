---
title: "home partition?"
date: 2011-01-03
forum: General Help
---

### Post by garyed on 2011-01-03
I'm getting ready to do a new install & looking for some tips about how to add a home partition. I've done a bunch of installs starting at 6.x but have never used a home partition. I was even wondering if you could put a home partition on a completely separate drive too. Does it mean that if I upgrade at a later time I can use the same home partition for the upgraded version?

---

### Post by mick222 on 2011-01-03
Not sure about putting on a different drive but it's easy to do and you keep all your data after a new install.

---

### Post by oldfred on 2011-01-03
While you could put it on a different drive, I would not. You want each drive to be independent, with MBR and all system files so that if one drive fails you can boot the other. If you have multiple drives I would install at least a minimal system on the other drive, and use it for backups or other data.

I have 3 copies of Ubuntu on two drives and XP on a third. I keep my old copy of Ubuntu and have another root for the beta to test, but try to make sure I have a working copy on each drive. I do not use /home but a /data, so I can use it in all my installs.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by msandoy on 2011-01-03
The file system in Linux is quite uniqe, you can add and remove drives as you want. As long as you know how the system is set up yourself, no problem. I used to have an old computer with a 20gb HD for root partition, and two 80gb HD's set up with software RAID as home partition. This worked really well, since it doubbled the speed of all my data in home, and I usually keep my games and such in /home/user/bin.
My usual setup consists of approx. 20gb partition for root, and everything else in a separate partition mounted at home. This means I can re-install or upgrade as I want without loosing anything in home.

---

### Post by nothingspecial on 2011-01-03
I`ve never used more than 12G for /

But then I dont have Ubuntu and Kubuntu etc installed.

During the partition stage
[SIZE=3][COLOR=Red]
I am assuming you are wiping the disk and have backups, if not ignore this[/COLOR][/SIZE]

Create 3 partitions, one about 12 gigs, one the rest of the drive leaving 2 gigs at the end for another.

During the partitioning bit of the install, choose manual (advanced).

Then choose the 12G? one

choose to use it as an "Ext4 journaling filesystem"

give it a mount point of /

choose to format.

Then choose the 2G one

just choose to use it as swap

Choose the remaining partition

use it as an "Ext4 journaling filesystem"

give a mountpoint of /home

and choose format.

That`s it.
[SIZE=4][B]
NOW[/B][/SIZE]

Any time you reinstall, do exactly the same except
[COLOR=Red][B]
DO NOT CHOOSE TO FORMAT THE /HOME PARTITION[/B][/COLOR]

---

### Post by garyed on 2011-01-03
Ok so does that mean if I later want to install Ubuntu 11.x along side my 10.04 I can add another partition for \ & use the same home partition for both?

---

### Post by hawkmage on 2011-01-03
Yes, but you need to make sure that when you create the users with the same numeric UID and GID.

---

### Post by nothingspecial on 2011-01-04
> **garyed said:**
> Ok so does that mean if I later want to install Ubuntu 11.x along side my 10.04 I can add another partition for \ & use the same home partition for both?

That`s what I do to test development versions.



> **hawkmage said:**
> Yes, but you need to make sure that when you  create the users with the same numeric UID and GID.

The easiest way to accomplish this to make sure you create the users in the same order.

So say you have garyed as your main account but also have "wife" and "kids" account. After your original install you created "wife" then "kids". When you install 11.04, create garyed during the installation, then create a "wife" account followed by a "kids" account.

As long as you do that the UID and GID will be the same.

If you have alot of users and you can`t remember type
```

less /etc/passwd
```

And you will see that you are 1000:1000

wife is 1001:1001
kids is 1002:1002

etc, etc, etc

---

### Post by randiroo76073 on 2011-01-04
I've got a slightly different take since I multi-boot regularly. I partition my first HDD1(sda)250gb to be able to put 6 distros on, 20gb per + swap + unallocated(in case I want more). HDD2(sdb)1tb is partitioned as /home(250gb), archives(the rest). All my distros use the same home partition to cut down on duplication of folders: Documents, Downloads, Music, Pictures, Public, Templates, Videos, Wallpapers(has saved me alot of disk space when hopping) My "user" in each distro is: my first initial + distro name. Works well for me,YMMV tho.

---

### Post by hawkmage on 2011-01-04
> **nothingspecial said:**
> 
The easiest way to accomplish this to make sure you create the users in the same order
I take a slightly different approach since I use different versions of Unix/Linux.  Some start UID/GID numbering at 100 (Solaris), 500 (RedHat) and 1000 (Debian).  So what I do is start my UID/GIDs manually at 2000.  When I install a new system I create a temp account durring the install.  Then use this account to create my real account with the UID/GID I want.

---

### Post by garyed on 2011-01-04
I guess what I don't understand about using the same home partition for different versions is what about the same programs that are also running on different versions. Say I've got Firefox installed with flash player in Ubuntu 7.10 & now have Firefox also on 10.04 & then install flash player.
I know some settings get stored in the home directory so won't they conflict.

---

### Post by randiroo76073 on 2011-01-04
The settings for most apps are stored in /home/user(your login name)folder. For instance, in my /home partition I have folders named: rfedora, rsuse, rzorin, rpinguy, rnetbook, rmaverick, + the shared folders I mentioned in my other post. The "r..." folders hold my app settings for the different distros and don't let them get mixed up.
Hope that helps to clear it up some.

---

### Post by garyed on 2011-01-06
Thanks for all the ideas, I installed Ubuntu Studio 10.04 & everything worked out fine.
I ended up using 15 gig partition for "/", 2.5 gig for swap & the rest for "/home"

---

### Post by uperpar on 2011-03-09
I would like to move /home back to the same partition as /.

My /home is mounted on a separate partition ( /dev/sda7), now I would like to move it to / /, which is /dev/sda6, so that I can reformat the partition to NTFS.......

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
/dev/sda7 on /home type ext4 (rw)

Thanks

---

