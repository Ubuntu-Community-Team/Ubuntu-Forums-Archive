---
title: "Making the Switch!"
date: 2009-11-11
forum: General Help
---

### Post by Neezer on 2009-11-11
I think I'm ready to make the switch completely! I have been running Ubuntu only for about 2 months on my dual boot laptop. I can't even boot into windows since I put Ubuntu on but that is another topic which doesn't matter anymore anyways.

I'm looking to remove the windows partition from my laptop and run with just ubuntu on the whole thing...It will give bee 300 more GB of hdd space.

How does one go about deleting the windows partition? Can I do it and keep the same Ubuntu install (9.04) that I have?

---

### Post by errol1 on 2009-11-11
Hi,
 
I only started with Ubuntu about 2 days ago.  How did you get your internet to connect?  I thought it would be easier, but I find it very difficult.  Maybe I can't answer your problem, but maybe you can help me with mine.  I have a wireless connection and on Windows I use Pop 3 etc, but on Ubuntu I don't see or know how to complete this.....I am lost!!

---

### Post by Wim Sturkenboom on 2009-11-11
@errol1, please start your own thread. It eventually becomes very confusing and frustrating who is answering who and on which issue.

---

### Post by Wim Sturkenboom on 2009-11-11
Neezer, can you post the output of *sudo fdisk -l* (that's lowercase L at the end). You don't have to re-install Ubuntu.

PS
With fdisk, you can change the type of the Windows partition to Linux. Next you can run mkfs.ext3 to format it as an ext3 partition. All can also be done with a partition manager (wait till somebody comes along that knows more about that).

---

### Post by Neezer on 2009-11-11
Here is my fdisk

```

nathan@lappy:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf9bc167

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40492   325250966    7  HPFS/NTFS
/dev/sda2           47014       48641    13075456    7  HPFS/NTFS
/dev/sda3           40493       47013    52379932+   5  Extended
/dev/sda5           40493       46741    50195061   83  Linux
/dev/sda6           46742       47013     2184808+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Is this all one hard drive with multiple partitions on it??
sda is the disk and sda1, sda2, sda3 etc. are the partitions?

If I had another hdd it would be sdb? I first did the command with an external drive plugged in, but I removed it cause I didn't want to cause confusion. It was labeled as sdb.

---

### Post by Neezer on 2009-11-11
Just wondering if anyone has any input on this issue. I'd like to get this done today, but I'm really not sure where to start.

I tried
```

gksudo parted

```

that didn't go over very well at all...my command line got all screwy and looked like the bottom line was getting written to over and over again really fast....had to close the terminal and open another.

---

### Post by Wim Sturkenboom on 2009-11-11
You have one hd (sda) with 2 primary partions (sda1 and sda2) and 1 extended partition (sda3). The extended partition contains 2 logical partitons (sda5 and sda6). A second HD will indeed be sdb.

Before doing the following make sure you have backups of all important data and you need to unmount the partitions that you want to change. I did not in the example below and therefore I got the warnings.

```

wim@desktop1:~$ **sudo fdisk /dev/sda**

The number of cylinders for this disk is set to 30515.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): **[COLOR="Red"]p[/COLOR]**

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e192e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       26892   189791910    f  W95 Ext'd (LBA)
/dev/sda5            3265        7180    31455238+   7  HPFS/NTFS
/dev/sda6            7181       10444    26218048+   b  W95 FAT32
/dev/sda7           10445       13708    26218048+  83  Linux
/dev/sda8           13709       13838     1044193+  82  Linux swap / Solaris
/dev/sda9           13839       26892   104856223+  83  Linux

Command (m for help): **[COLOR="Red"]t[/COLOR]**
Partition number (1-9): **[COLOR="Red"]1[/COLOR]**
Hex code (type L to list codes): **[COLOR="Red"]83[/COLOR]**<enter>
Command (m for help): **[COLOR="Red"]w[/COLOR]**
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
*The new table will be used at the next reboot.*
Syncing disks.
wim@desktop1:~$

```I'm not sure which partition you want to change, in the example above I took the first one. You can also do the second partition before writing to disk (w). If you get the warning, modify fstab as described below and reboot.

This should be sufficient.

Next you can format
```

mkfs -t ext3 /dev/sda**[COLOR="Red"]1[/COLOR]**

```

You also need to modify /etc/fstab. I suggest that you put a # in front of the lines that refer to your partitions that you have modified.
```

# /dev/sda1 -- converted during upgrade to edgy
**[COLOR="Red"]#[/COLOR]**UUID=2020F32C20F30814 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

```
That should be it.

Next we can discuss how you actually want to use it. You can mount it as e.g. /home or mount it in your home directory.

PS the reason for the # in /etc/fstab is that it comments out the line. Therefore you will not get errors when (re)booting the system (as it would try to mount an ext3 partition as ntfs or so).

---

### Post by Neezer on 2009-11-11
Thanks for the reply....before I get too deep and can't get back,

Will this setup give me a separate partition or will it just remove the windows partition and make it part of my existing ubuntu partition?

I am assuming that the two NTFS partitions that I have are my main vista and my system restore that it came with...If I go through this process using 2 for the partition number will that change the system restore one as well?

I just really don't want to muck this up and end up reconfiguring all my audio/video options that I had to do to get it working.

---

### Post by Wim Sturkenboom on 2009-11-11
I did edit my post slightly, so reread it, please. This will only format the partition(s) that you touch. They will not even be visible in 'places'.

So the question is how you want to use it. Personally I would make sda1 the /home partition, but as said before, you can make it a directory in your home directory or a directory in /media (as the current situation probably is).

And a question from my side is what is sda2?

OOPS, did not read your comment on sda2. It might well be the restore partition although it's a bit big (13GB). In that case you can no longer restore.

---

### Post by Neezer on 2009-11-11
> **Wim Sturkenboom said:**
> I did edit my post slightly, so reread it, please. This will only format the partition(s). They will not even be visible in 'places'.

So the question is how you want to use it. Personally I would make sda1 the /home partition, but as said before, you can make it a directory in your home directory or a directory in /media (as the current situation probably is).

And a question from my side is what is sda2?

I think sda2 is just the system restore partition that came pre-loaded on my laptop for vista. Either that or it is the actual install of vista and the other partition is the storage partition for it. I didn't really pay any attention to it so I'm not 100% sure.

anyway, 

I went through and did the fdisk thing...and reformatted the partition. What is fstab and what does it do?

When I go into fstab I don't have anything that refers to sda1....just sda5 and sda6, My main ubuntu partition, and my swap partition.

```

 /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=912a7fe6-d7de-473d-a010-f447e52247ce /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8c66457a-a3d5-4eff-82cf-e87272bc6909 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by Neezer on 2009-11-11
I'm afraid to reboot my computer at the moment cause I was doing some google searching and found gparted....started it up and found that my boot was on sda1. Now it isn't there at all....So I don't know if I'll be able to boot up or not if I try to restart!

I love Linux! The worst that happens is I become a little more familiar with how to get my sound working on my laptop!

---

### Post by Neezer on 2009-11-11
Sorry to get my panties all in a bunch...I went to get my live CD and rebooted fully expecting to need it and voila! it worked!

This is what I have....
```

nathan@lappy:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcf9bc167

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       40492   325251958+  83  Linux
/dev/sda3           40493       47013    52379932+   5  Extended
/dev/sda5           40493       46741    50195061   83  Linux
/dev/sda6           46742       47013     2184808+  82  Linux swap / Solaris

```

I also don't have sda2 on there anymore cause I made it unallocated in gparted in an attempt to try and merge the freespace with sda1, but I couldn't figure out how to do it.

I guess now I need to just figure out how to mount sda1. It was in /media when it was a windows partition.

I don't really know what my options are for mounting...discuss?

---

### Post by Wim Sturkenboom on 2009-11-12
> **Neezer said:**
>  What is fstab and what does it do?
I think it stands for **f**ile**s**ystem**tab**le


Check /media; it might contain a subdirectory sda1. If not, you can create it. For testing purposes you can place a small file in /media/sda1.
```

sudo mkdir /media/sda1
sudo touch /media/sda1/tmpfile1

```*ls /media/sda1* will show you tmpfile1

Next you can mount with the *mount* command for testing; later you can make it permanent.
```

sudo mount -t ext3 /dev/sda1 /media/sda1

```*ls /media/sda1* will no longer show you tmpfile1
You can unmount with the *umount* command and ls will show you the tmpfile1 again.

As you don't have a separate home partition at this moment, I suggest that you use your new partition for that. I'm not behind an Ubuntu machine at the moment, so can not check what the entry in fstab is supposed to be.

The basic steps are:
[LIST=1]
[*]use single user (recovery) mode
[*]mount the partition as shown above
[*]copy the contents of /home to /media/sda1 using *cp -R -p*
[*]for testing create a new file in your home directory
[*]unmount the partition and remount on the home directory (so instead of /media/sda1 use /home)
[*]your test file in your home directory should have 'disappeared' and all other files should still be there
[*]create an entry in /etc/fstab so the partition will be mounted on /home at boot time
[*]reboot
[/LIST]
If everything works, reboot to single user mode again, unmount the home partition and check in your home directory for the existence of the test file as that will prove that the partition is indeed unmounted. Next delete the current contents of /home to make the space available for other stuff. Reboot and you should have a fully working system with a seperate home partition.

---

### Post by Neezer on 2009-11-12
I guess I'm a little confused as to the benefits of making this partition /home.

If I put my 80GB of music into the new /home/nathan/Music folder, would a different user be able to play it?

---

### Post by Wim Sturkenboom on 2009-11-12
It will be the same as with your current setup. The advantage of a separate home partition is that a re-install of the OS will not wipe all your 80GB of music (amongst all other data) as you don't have to format the home partition, only the root partition (in your situation).

---

### Post by Neezer on 2009-11-12
So I am in root/recovery mode now and posting from my blackberry. I have a root prompt and no gui?

I am trying to do
```

cp -R -p /home /media

```

Right now my extra partition is mounted on /media. It is taking a long time. It has been going for about 10 minutes now and I am not getting thw prompt back. 

Is something going wrong?

---

### Post by Wim Sturkenboom on 2009-11-12
And the last missing piece of info (post #13, point 7); this is take from my system.
```

UUID=6f2c3bef-9ed8-4be1-83be-005931de05dd /home ext3 defaults 0 2

```

You must change the uuid; to determine it, use *vol-id*

```

wim@desktop1:~$ **sudo vol_id --uuid /dev/sda1**
6f2c3bef-9ed8-4be1-83be-005931de05dd
wim@desktop1:~$ 

```

---

### Post by Wim Sturkenboom on 2009-11-12
I'm not sure how much you're copying but it can take a while. And there is unfortunately no progress indication

---

### Post by nothingspecial on 2009-11-12
If you use the -v flag, cp will tell you what it`s doing.

If you have a large music collection and have used cp without -v then it will just blink at you until it`s finished.

Have a look at /media. Is there music in there that wasn`t before? In that case it`s working.

---

### Post by Wim Sturkenboom on 2009-11-12
> **nothingspecial said:**
> If you use the -v flag, cp will tell you what it`s doing.
Stupid me, I have the man page open in front of me to check for that option and did not see it ](*,)

---

### Post by Neezer on 2009-11-12
Thanks for all the replies! I really appreciate it! And that -v flag will come in useful. 

I am so close and need just a tiny bit more help. 
When I rebooted with the proper mount point put into fstab I got an error upon logging in...something about not having a home folder so I chose to create one. 

After investigating I found that I have a /home/nathan

This one was created when I logged in without a home folder. This is not my normal home folder. 



I also have a /home/home/nathan folder. This one contains my original user profile and everything. 

I am back in recovery mode and I know what I need to do, but I'm getting confused with what command I should use to copy /home/home/nathan so that I end up with /home/nathan 

Maybe I can just rmdir /home/home, but I don't want to do that until I know it won't muck things up. 


I really want to thank all of you for the help. I know that you are doing this just because you enjoy it and you don't have to and I really appreciate it! THANK YOU!

---

### Post by Neezer on 2009-11-12
Really sorry to be double posting, but I know that I can really screw things up if I do something wrong as root.


anyways, that is all behind me cause I got it to work!!!!


first i just deleted /home/nathan and all its files

then:
used the following to make /home/nathan with my original stuff!
```

cp -R -p -v /home/home/nathan /home

```

Thank you so much for all of the help! going through exercises like these is how I learn cli, and I feel a lot more confidant about some things...

Again, I really appreciate the help and quick support that I've gotten here.
Thank You


**EDIT:** So I marked this as solved, but I have one more quick question...I have two things in my GRUB that refer to Vista and I have reformatted the partitions, so I do I get GRUB to just show my Ubuntu boot options? I have 3 Ubuntu kernels and 3 kernel recovery modes as well...can I change GRUB to get rid of the old kernels as well?

---

### Post by Wim Sturkenboom on 2009-11-12
Yep. The entries are defined in /boot/grub/menu.lst

---

