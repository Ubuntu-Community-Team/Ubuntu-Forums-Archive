---
title: "Need help to Partition Hard Drive"
date: 2010-09-27
forum: General Help
---

### Post by Mingan on 2010-09-27
I believe that Ubuntu/Linux is better then Microsoft XP and I want learn to run my own computer and soon learn network admin. with Ubuntu Server.

I have run Ubuntu on a separate older computer for 6 months that I had to leave behind when I moved, and got a New Computer, which I need keep XP on and make it a duel boot.  The desk top course I took from Canonical to try to learn to Partition the Hard Drive isn't helping, as it wants me to redo  the drive and I cant do that.  SO I need to know how do I Partition my terabyte drive and keep windows on it? 

I downloaded and burned to disk 10.04 and it is confusing me I don't know if I can use it to do the partition with as I don't know how to.  I may wait till Oct 23 for the new 10.10 Ubuntu, but want to learn to do the partitioning before then if I can.

Any help?

System: 
Microsoft XP Professional
Version 2002, Service Pack 2

Computer:
Intel(R) Core(TM)2 Extreme
CPU Q67850 @ 3.00GHZ
3.00 GHz 3.25GB of RAM (has 4GB RAM but xp cant see it) 
Physical Address Extension

---

### Post by harrismh777 on 2010-09-27
:-\"

Ok, partitioning for linux is for experts only. (seriously)

If you have never done it, do not try it on a machine you care about.

Having said that:

   The best way to proceed is to let ubuntu installer partition the hdd for you by default. It will resize the partition holding windows, install ubuntu on the remainder of the drive and setup a dual boot (grub2) loader that will allow you to select XP or ubuntu. 

   Do not try to custom partition your drive... and not from advice on this forum either. Read the on-line tutorials, and find yourself a good book on system administration. I can recommend this one:

   O'Reilly's Running Linux 5th addition or higher....

   or

   Maximum Linux Security    by anonymous
    a hackers guide to protecting your linux server and workstation

   Also, the best way to setup a linux distro is to have multiple partitions... about 12 of them...  one for each mount point
 /
 /boot
 /usr
 /opt
 /home
 /var
 /tmp
 /usr/local
                and there are others....

    This is covered in Maximum Linux Security

Again, don't try to partition your system for linux unless you know what you are doing. Let the installer do it, and enjoy.


[-o<

---

### Post by sikander3786 on 2010-09-27
If you want the simplest partitioning setup, just free up some space on your HDD say 30GB, leave it unallocated i.e, don't create any partitions on it and during the Installer's partitioning step, choose "Use largest continuous free space". Thats it. /root and swap partitions will be automatically created by the installer and Ubuntu will be installed to that.

As harrismh777 suggested above, you can have separate partitions for /boot, /root, /home etc etc. But it is an advanced setup.

> Do not try to custom partition your drive... and not from advice on this forum either.

The community is not that bad :-) I agree that sometimes you get answers off topic and immature, but you can go through all the responses and pick the best one. And that one definitely works I believe.

---

### Post by Quarkrad on 2010-09-27
I (newbie to Linux) have successfully, a number of times on different machines - installed Ubuntu on PCs that started with a windows only on them.

[LIST]
[*]Used a native win partitioning app (e.g. Partition Magic, Partition Manager) to create a new NTFS partition 
[*]Made a note of the unique size of this empty new partition*
[*]Insert the Ubuntu installation LiveCD and rebooted
[*]Followed the prompts to install Ubuntu choosing the manual option when it come to what partition to install Ubuntu on
[*]Choose the new NTFS partition to install to and click the option to reformat the partition to ext (ext 4 for Ubuntu 10.04)
[*]The install process identifies winxP (which you choose to include in the boot) and you sit back
[*]When it finishes you are prompted to take put the CD, the pc reboots and you get a grub screen offering you which OS to boot to.
[/LIST]

* Actually I create two partitions - one for the Ubuntu OS an another (at the end of the HD) for the linux SWAP.

I have never lost any data or failed with this process but perhaps I have been lucky.  Back up any important win data and have a go.  _If_ for some reason the grub dual boot screen goes a bit AWOL there is plenty of solutions on the net on how to fix these issues.

---

### Post by Ghost_Mazal on 2010-09-27
> **harrismh777 said:**
> 
 
Also, the best way to setup a linux distro is to have multiple partitions... about 12 of them... one for each mount point
/
/boot
/usr
/opt
/home
/var
/tmp
/usr/local
and there are others....
 

 
Harrismh777 , why do you say that ? I know why /boot and /home is good to be seperate , but why the others too ? That made me very curious.

---

### Post by Mark Phelps on 2010-09-27
You don't NEED 12 partitions!  Good grief!!

You only NEED two partitions -- one for root and one for swap.  And, some will argue that you can get by without a swap partition and use a swap file instead.

For added flexibility, you could create a third partition, this one for /home.  That will allow you to upgrade to newer Ubuntu versions without losing your saved files.

---

### Post by Dr. C on 2010-09-27
One suggestion is to defrag the Windows partition before resizing using the Ubuntu live CD. [UltraDefrag]("http://ultradefrag.sourceforge.net/") is a great Windows defragger and is FLOSS. It goes without saying back up the Windows computer first.

---

### Post by srs5694 on 2010-09-27
> **sikander3786 said:**
> Thats it. /root and swap partitions will be automatically created by the installer and Ubuntu will be installed to that.

I'm afraid you've made an error in your terminology. The names are confusing, so such an error is understandable, but it's an important point: Linux requires a partition whose name is pronounced "root" and that's referred to on the command line as "/". All the files on the computer are referred to relative to this "root" directory. The root directory (or partition), however, is entirely different from the /root directory, which is the superuser's (root's) home directory. Although the computer would probably boot with a separate /root partition, you should not split it off. The reason is that, in some emergency situations, the root user must be able to log in even if the computer is having problems mounting anything but the root (/) partition, and to do that, having /root as part of the root (/) partition is helpful. (This can apply even to Ubuntu; despite the lack of root login support once everything is up and running, emergency single-user mode still uses the root account for logins.)

[quote=Ghost_Mazal]Harrismh777 , why do you say that ? I know why /boot and /home is good  to be seperate , but why the others too ? That made me very curious.[/quote]

There are quite a few reasons for splitting off various directories into their own partitions. These include enabling booting (from /boot) when using RAID, LVM, or ancient BIOSes that can't read all of a modern hard disk; the ability to use different filesystems to optimize performance; protecting data from filesystem errors in different partitions; mounting some partitions (such as /usr) read-only for security purposes; using mount options like noexec to prevent program execution or to enable other filesystem features on a directory-by-directory basis; keeping runaway growth of files from affecting other directories; and protecting data on certain partitions (/home and /usr/local, for instance) from destruction should you want to do a full re-installation of the OS in the future. I wrote [an article for IBM developerWorks](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html) on this topic a while ago; consult it if you want more details.

That said, a typical home installation of Ubuntu doesn't *need* so many partitions, and creating so many partitions is likely to cause more problems than it solves, in terms of getting the sizes right and dealing with the mechanics of it all. IMHO, a typical home user can benefit from three partitions: root (/), /home, and swap. Using more than that requires good specific reasons. Professional system administrators typically understand the issues and have the reasons, but typical home users don't. There are sometimes exceptions, though. For instance, one of my Ubuntu installations is on a MythTV box. I've got its recordings directory on a separate partition (actually a logical volume) to protect its recordings, similar to the logic for a separate /home partition. Furthermore, I've got a separate partition for the directory where MythTV puts its DVD-creation log files, because on rare occasion the DVD-creation process spins out of control and keeps writing to the log file until the disk fills up. The trouble is that MythTV then starts deleting recordings to make room on the disk, so when the DVD-creation process flakes out, it deletes all the recordings! Putting the DVD log directory on its own partition protects my recordings, even though that partition only holds a handful of files, and is itself very small.

---

### Post by harrismh777 on 2010-09-27
> **Ghost_Mazal said:**
> Harrismh777 , why do you say that ? I know why /boot and /home is good to be seperate , but why the others too ? That made me very curious.

Ghost-Mazal,

srs5694 is correct, and I will add a couple of points. For a more complete discussion of the topic please see Maximum Linux Security by anonymous.

The primary reason for splitting off the primary mount points with unique partitions is security, but also this is done for backup, recovery, and update. For instance, if you machine goes down "unclean" leaving disks umounted "unclean" (power failure, multiple storm) it won't honk the whole system... usually just /var and /tmp. The machine will still boot allowing the admin to fix /var and /tmp mount points and recover easily. Or, suppose you want to reload the entire setup with another distro, or with the same distro from scratch, but you want to keep you /home directory. If /home is on its own partition then the reload (and repartition) can be secured without having to reload (or lose) /home. Or,
suppose you want to secure your multiple user machine at home (this is my own case) so that your family can share it, and you want the /home directory to be mounted nosuid, to protect it from running programs with root authority; /home on its own partition can be mounted with security options that protects the machine better than if /home was on the same partition as /usr/bin, etc. 

Or, suppose you want to multiboot your machine (several linux distro's) and have them all SHARE the /home directory. If /home is on its own partition you can have any of the distros mount /home so that there is just one copy of your personal files on the physical hardware available to each of the distros you may want to boot into. 

If planned correctly file access can be greatly increased depending on where you place swap (on its own partition) and where you place / /usr etc.

The reason the machine usually ends up with 10 - 12 partions is that /boot should be on its own partition too, and there needs to be a virtual or extended partition in the fourth position on ide drives. By the time you spread out the mount points, provide the extended partition, and have a separate partition for /boot, you'll end up with about 10 - 12 parts.

The reason you may want /boot on its own partition is that it doesn't need to be journaled. /boot can be etx2 for that matter!  In the old days we would put /boot on its own partition because the bootable partition needed to be within the first 1024 blocks. Today this is not the case, but its still a good idea to have /boot on its own partion so that it doesn't get honked on power failure etc.


Hope this helps.
):P

---

### Post by Ordes on 2010-09-28
> **harrismh777 said:**
> 
Ok, partitioning for linux is for experts only. (seriously)


Yes & No, the problem is there are home-users and pro-users; 
from a pro-user point of view i agree with you; 

however i dont think basic home-partitioning is for experts only. when you have a little pc-knowledge the task shouldnt be to hard. with home-partitioning i mean mostly /, /home, swap. Whereas /home is mostly for the cause of backup, and or system restore ( > formatting /, etc)

specially when u about to install a fresh ubuntu it cant get easier:

1. load up ubu-live
2. use gedit to make the partitions /, /home, swap (keep note of the names; sda1, sda2, etc)
3. load up ubuntu installer; when it comes to setup beside windows/ partitioning, choose manual
4. choose the sdXX for /, /home, and swap; +file system +format y/n
5. setup grub, the default settings should be ok
6. finish instalation

---

### Post by sikander3786 on 2010-09-28
> 
I'm afraid you've made an error in your terminology


I accept my mistake :-) It should have been "/" and swap. Thanks for pointing out.

---

