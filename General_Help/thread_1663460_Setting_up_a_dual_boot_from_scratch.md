---
title: "Setting up a dual boot from scratch"
date: 2011-01-09
forum: General Help
---

### Post by dirtynorth on 2011-01-09
Hello all,
 
From what I have read around the net I should be able to set up my hard drive so that I have one small partition for Windows 7, one small partition for Ubuntu 10.04 and the remainder can be a third partition which contains all my files (accesible from both OS).  first question, is this possible?
 
 I tried to install Windows 7 first (I hear installing Ubuntu first creates havoc), then i tried to use the partition editor that comes with windows 7 and it wont let me shrink the partition any smaller than 700GB even though it is 98% free ( I have tried defragging thatdrive).
 
Now Im wondering, can I use GParted to format my disk, then set up all the partition, and then install the OS's?
 
If so how would I do this?
 
Thanks and Sorry for the long post

---

### Post by TeoBigusGeekus on 2011-01-09
> **dirtynorth said:**
> ...first question, is this possible?

Of course it's possible. Just format it as ntfs.

> **dirtynorth said:**
> Now Im wondering, can I use GParted to format my disk, then set up all the partition, and then install the OS's?
 
If so how would I do this?

Although it's better to do the partitioning from win7, you can boot up with an ubuntu live cd and use gparted.
After you finish, try to boot win7 to see whether it's ruined or not; in case of the latter, you can proceed with the ubuntu installation.

---

### Post by dirtynorth on 2011-01-09
Thanks, Ill give that a try

---

### Post by dirtynorth on 2011-01-09
okay,
 
I think the re-sizing of the Windows partition worked.  I assunme being able to boot log in and acess theese forums is a good enough test that I didnt destroy Windows.
 
Now, How large of a partition should I use for linux?  and What file system should i use for my data partition so that it canbe accessed by windows and ubuntu?

---

### Post by dirtynorth on 2011-01-09
Sorry, alrerady answered the second question, ntfs, duh!

---

### Post by TeoBigusGeekus on 2011-01-09
10~15gb for / is perfect.
20~30gb for /home is OK (this one depends completely on you).
1~1.5gb for swap should be enough.
Format the rest as ntfs and give as mount point during installation something like /media/DATA (so that you don't have to fiddle with fstab after the installation).

---

### Post by dirtynorth on 2011-01-09
I am a little confused.

I out the 10.04 disk in and went through the instalation.  I selected manually set up partitions and then I got fairly confused.

first: what is "/" "/home" and swap?
second: do I have to create a seperate partiton for each?
third: should the partitions look something like /dev/sda3  ?

---

### Post by TeoBigusGeekus on 2011-01-09
Create 4 new partitions.

swap
Linux pseudo-ram, something like page file in windows. Whenever things get tough on your system, ram wise, ubuntu will use this space as extra ram. Give its use as swap space - the installer will gray out all other options.

/
Root partition; everything starts from there. The place where the main installation will take place. Format it as ext4, give / as mount point.

/home
Your home partition; this partition will hold your user settings. It is a good idea to have a separate home partition: in case of a re-installation, you can keep using the same home partition without formatting it, thus maintaining all your settings (settings, mind you, not applications). After the re-installation, you will magically see your old settings applied to every single installed application you used. Format it as ext4, give /home as mount point.

/media/DATA
Your shared data partition. Format it as ntfs and give /media/DATA as the mount point (you can replace DATA with whatever you like - no spaces, please :P).

Finally, yes, the new partitions will look something like /dev/sda3.

---

### Post by dirtynorth on 2011-01-09
How large of a swap partition?  I have 4Gb ram, if that matters.

---

### Post by TeoBigusGeekus on 2011-01-09
You shouldn't need any swap with 4gb, but make it 1gb, just in case...

---

### Post by dirtynorth on 2011-01-09
Im in the ubuntu installer and i have created:  /,   /home and swap.   I cant seem to get the fourth one though because ntfs is not an option under the "use as" menu

thanks again for all the help

---

### Post by TeoBigusGeekus on 2011-01-09
How many partitions do you have altogether in your hard disk (including windows partitions)?
Are they all primary?
You might need to create an extended partition.

---

### Post by dirtynorth on 2011-01-09
I have:

/dev/sda1   ntfs  100MB                 was created when I installed windows
/dev/sda2   ntfs  ~35GB                 where windows is
/dev/sda5   swap  1GB
/dev/sda6   ext4  15GB                  /  mount point
/dev/sda7   ext4  30GB                  /home  is the mount point

As far as primary is concerned, I dont know which ones are which

---

### Post by TeoBigusGeekus on 2011-01-09
Abort the installation, reboot with the live cd and, using gparted, delete sd5, 6 and 7.
Then right click the unallocated space (should be your hd-sda1-sda2), create new filesystem. Create an extended partition.
Reboot then and try to install from scratch in the extended partition.

---

### Post by LewRockwellFAN on 2011-01-09
That is WAY more home than you need if you plan to keep your data in a common data partition. I can't see why you need more than 200 mb at most. Anybody who thinks I'm wrong, please enlighten me. You don't really need a home partition at all, although it is concievable it may make it a little easier if you install a new linux over the old one at some time in the future, particularly if you do a lot of tweaking and don't want to do it again for the new installation. Someone else should comment on that. I don't use a home partition at all.  If you don't use a home and just put everything in / you won't have to worry about how big to make it and you'll never have to resize it and probably never find some download choking because you accidentally put it in home rather than /media/data like you meant to.

---

### Post by oldfred on 2011-01-09
The OP must have an extended partition. sda1 thru sda4 are the primary and one becomes the extended which is the container for sda5 and up which are all logical partitions.

The NTFS data partition can be either primary or logical. Windows only has to have a primary to boot from.

---

### Post by dirtynorth on 2011-01-09
worked perfect!

Big Thanks to [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094") for the help.  

Im not too concerned about space, I still have over one Tb left and Im sure the home directory will come in useful as I am prone to tinkering with things I have no reason to tinker with.

Thanks for the help everyone

---

### Post by TeoBigusGeekus on 2011-01-09
> **dirtynorth said:**
> ...I am prone to tinkering with things I have no reason to tinker with.


That's the spirit!!!! :P

---

