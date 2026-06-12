---
title: "Cant mount 2nd Hard Drive"
date: 2010-08-24
forum: General Help
---

### Post by barnesey on 2010-08-24
I have got 2 hard drives running one one of my computers which i am running as an server. I was using Ubnntu Server which is good but i have decided to change the way that i am going to use the server and have installed Xubuntu over ubuntu server.

However in the installation the hard drives shwn when it asked where i would like to install the operateing system. It installed sucessfully and is working but it cant mount my other hard drive which has all of my data on it.

I had tried mounting it throught the command prompt and had no success. After which i have checked if the the toher hard drive is being reconised by Xubuntu and it is as sdb1 but i caqnt mount it and get to my data.

I hoped that i can try and put in my ubuntu live cd and see if it can pick the seoncd hard drive up and mount it which it has not been able to.

I have 2 20 gigabyte hard drives atm the moment and i am not adding the others until i can get to all my stuff again form the other hdd.

Thanks in advance.
barnesey,

---

### Post by MilesTails on 2010-08-25
Is it giving you any kind of error message when you try to mount the drive from the command line?

---

### Post by quixote on 2010-08-25
Yes, error messages, if any, would be useful info.  Another thing you could try is to run e2fsck on those partitions, assuming they're linux format, not vfat or ntfs.  You can use```
sudo fdisk -l  (*"l" as in list*)
``` to find out the drive designations.  Let's say it's /dev/sdb1.  Unmount it (sudo umount /dev/sdb1), and then run ```
sudo e2fsck -p /dev/sdb1
```Remember to substitute your own designation for /dev/sdXy.  The -p switch stands for "preen", i.e. automatically fix any errors found.

---

### Post by barnesey on 2010-08-26
The error message im an getting is 

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, 
missing codepage or helper program, or other error
In some cases usfel info is found in syslog - try
dmesg / tail or so

On the machines start i get an option to retry, skip or ignore mounting after adding it to the fstab see if it will work then. (Which it didnt lol)

Im am going to try and see what quixote suggested and see if that has any result of it working,

---

### Post by barnesey on 2010-08-26
I have now tried what quixote saild to do and the umount work well but when i typed in the 

```
e2fsck -p /dev/sdb1
```I got the following message

```
e2fsck: Attempt to read block from filesystem resulted in short read while teying to open /dev/sdb1
Could the be a zero length partition?
```Getting confused!!

---

### Post by -kg- on 2010-08-26
What were the results of "sudo fdisk -l"?  The results of that command will show what you're looking at as far as the partitions on both drives.

---

### Post by barnesey on 2010-08-26
Here is the results for the fdisk -l

```
This is the main HDD
Device Boot    Boot          Start               End               Blocks        Id      System
/dev/sda1         *                  1             2382          19130368        83      Linux
/dev/sda2                        2382            2492              877569         5       Extended
/dev/sda5                        2492            2492              877568        82      Linux Swap / Solaris

This is for the second hdd!!
Device Boot    Boot          Start               End               Blocks        Id      System
/dev/sdb1                           1             2491          20008926         5      Extended


```

---

### Post by MilesTails on 2010-08-26
Do you know what filesystem is on the second drive?

The default filesystem in ubuntu 10.04 is ext4 for which you can run:

sudo fsck.ext4 /dev/sdb1

otherwise you need to run the appropriate fs checker for your filesystem

---

### Post by barnesey on 2010-08-26
I think the file system on the hdd is ext3. Then the hdd had windows computerf connecting to the shares.

What will be the best way of getting to work 10.04

---

### Post by -kg- on 2010-08-26
Well, according to "fdisk -l" there is no file system on your second hard drive:

```
This is for the second hdd!!
Device Boot    Boot          Start               End               Blocks        Id      System
/dev/sdb1                           1             2491          20008926         5      [COLOR="Red"]Extended[/COLOR]
```

You can read this at the tutorial linked to in my signature block (along with quite a bit of other useful information on Partitioning operations), but an Extended partition is a special type of Primary partition used to overcome the "4 Primary partition" limit.  An Extended partition cannot be formatted with a file system.  Instead, you create partitions within the Extended partition (called Logical partitions) which themselves are formatted with a file system.

I don't know whether you had any information on that drive before, but you don't now.  You need to create Logical partitions within the Extended partition, formatted to your desired file system type, before you can access the drive.  Basically, there are no readable partitions on that drive, which is why you couldn't mount anything from that drive...there's nothing to mount.

If you had data on that drive earlier, I fervently hope you had it backed up.  You can then create a Logical partition (or partitions), format them, then copy the data back into the partitions.

If you didn't back the data up, there are methods that you can use that *might* recover your data, as long as you didn't overwrite it.  I'm not sure on these methods (there are some on this site that are quite good with it), but you definitely don't want to make any more moves with the drive until you go through the attempt to recover data.

If you have data to recover, you might want to start another thread with a descriptive title indicating what you need to do, like "Partitioning Error-Need to Recover Data From Deleted Partitions".

---

### Post by quixote on 2010-08-26
barnesey, the bad news is that errors like that from e2fsck tend to mean there's some kind of disk corruption, which is quite possible if Windows tried to write to it.  The good news is that there are ways to fix that, although it's never fun.

(I was unaware that e2fsck doesn't work on ext4.  It seems to work on my ext4 partitions.  ??)

Just as a for instance on disk recovery, so you can see what's involved, this is what I do.  Boot with liveCD or, better, LiveUSB which has some space allocated to save settings.  (Then you don't need to keep doing the same steps if you have to start over.  Start synaptic (System > Administration > Synaptic). Go to Settings > Repositories, and enable "universe" repository.  Reload repositories.  Then install "testdisk" and "photorec".

Run testdisk on /dev/sdb1.  There are step-by-step instructions [here]("http://www.howtoforge.com/data_recovery_with_testdisk"). You'd be starting a little way down Step 2, at "Now let's assume we have lost our partition table." The default choices in their example are the ones to choose in nearly all cases, including probably yours.  It's an ugly text-based program (which means it works on very broken computers), but it's very good.  (Do *not* get creative and try other options, such as "alter disk geometry."  You could blow up your drive completely.)

If testdisk does nothing for you, then one proceeds to get the data off using something like photorec.  That's discussed [here]("http://www.psychocats.net/ubuntucat/recoverdeletedfiles/"). 

Don't lose heart. :D  Fighting with uncooperative disks is both tedious and nasty, but I bet all that's happened with yours is Windows wrote over the partition table.  That's a very recoverable problem.

*Update;  (I just read -kg-'s comment above.  I think he's being a bit too pessimistic.  There are ways to recover an overwritten partition table, such as testdisk.  He's very right that you should try to access the drive as little as possible except for attempting recovery.)*

---

### Post by barnesey on 2010-08-26
The drive i was trying to mount is my backup drive as why i have changed to Xbuntu is that the hard drive with Ubuntu Server on it had failed. 
I dediced to make my server do more for me and easier to manage so i am going to go for running things vurtally as the machine it is running on is very capiable of running many vms at once.

However that is not the major point is that i dont have anything big enougth to get my data off onto something else. As far as i recall the hard drive was comeing up for full when ubuntu server went.

I have some other hard dirve but they are 10 and 5 gigabyte hard drives.

Also the machine i am running doesnt have support for have boot able usb devices. So i am in a little difficult situation, would there be any other ways of getting my stuff back.

---

### Post by MilesTails on 2010-08-26
> **quixote said:**
> 

(I was unaware that e2fsck doesn't work on ext4.  It seems to work on my ext4 partitions.  ??)

J
 
Im not sure if it does or not, you may be right and im just used to invoking it the other way ;)

barnesey, Hes absolutely right recovering a corrupted partition is possible, and test disk has saved my bacon a couple of times :)

If you cant boot to a usb disk I would recommend the Parted Magic live cd, which includes test disk and whole bunch of other tools. 

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by barnesey on 2010-08-26
I have tired some other software and it doent look promising so i am going to have do with out my data as there is nothing of critical importance will be lost only the minor back ups which i can make up again and some stuff im not worried about. Silly thing happen and we will have to live with them.

Anyway what would be the best way on setting up and partitioning the hard drive so i can share it with some windows and linux computers. 
Ive herd that win 7 is sometimes not nice with linux hosts but there ways of getting it to work (I hope anyway).
:lolflag:

---

### Post by MilesTails on 2010-08-26
I usually use a fat or ntfs partition for data and then seperate partitions for Win and Linux.

Also in my experience you want to set up windows first and then load linux afterwards..that way you dont have a problem with windows overwriting grub or anything fun like that. ;)

---

### Post by barnesey on 2010-08-26
The machine is running linux on the first hdd no windows the second hdd is for holding data for shares etc.

So basiclly could make it ntfs so it would work with linux and windows or is there any better way around that?

One ntfs drive will be eaiser i think.

---

### Post by The Real Dave on 2010-08-26
I almost jumped and suggested [my guide for repairing a damaged superblock in ext4]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/") (or 3), but in this case, I don't believe that's the problem.

PartedMagic is definitely the way to go, and if it can be done, testdisk will recover it. You may lose some data, you may indeed have a corrupted filesystem issue also. You can deal with that when you get to it though. 

The link above may help with a corrupted filesystem, and though it's a little premature, I'm posting it in case I forget to return to this thread.

Best of Luck :)

---

### Post by MilesTails on 2010-08-26
You could certainly install windows on your second drive with your data and then install linux on your other drive if thats what you mean. Your data just has to be on ntfs for both to be able to use it.

---

### Post by quixote on 2010-08-26
Try testdisk for your 20GB drive before giving up on it.  If it's not the end of the world if it doesn't work, then you haven't lost anything by trying.  From enabling the repos, through the end of running testdisk, it'll take you maybe half an hour.  Honestly.  Give it a whirl.

Re partitioning: Windows won't handle anything except vfat or ntfs.  And it has to be installed first, if you want an easy life.  Linux can access just about anything, except some MacOs (hpfs) partitions take some work.  Not your problem, I gather.  Linux root, or system, files have to be on ext2, ext3, ext4, reiserfs, and the like. Keep it simple: use ext4.  I believe the /home dir also has to be a native linux-type filesystem, but other filesystems can be mounted on it.  See next....

So, set up ext4 partition for linux root (/), ntfs for Windows if you need it, ext4 for separate linux /home (a good idea to have that on a separate partition), and a vfat or or ntfs partition for data.  When you're all done, you can mount the data partition to a directory under /home/your-user, and you won't even have to notice it's a separate partition with its own filesystem.  But Windows will be able to access it without complaining.

---

### Post by MilesTails on 2010-08-26
> **The Real Dave said:**
> 
The link above may help with a corrupted filesystem, and though it's a little premature, I'm posting it in case I forget to return to this thread.

Best of Luck :)
 
Thanks for that link I am bookmarking it for future reference :D

---

### Post by The Real Dave on 2010-08-26
> **MilesTails said:**
> Thanks for that link I am bookmarking it for future reference :D

I'm glad to hear that :)

---

### Post by barnesey on 2010-08-26
Ok then i will try TestDisk Tommorow.

If all fails and buy the sounds of thing dosnt sound like it, and looking at The Real Daves page it would work.

What i am trying to achive is my Xubuntu Machine would be my server and i want to make shares for both Windows and Linux (No macs as i think there rubbish and u can get much better for free. Thanks Linux and The Ubuntu Distros as well, So Macs i dont care).

I am going to make some VM's so i can have more flexable management of some of the stuff i want to run and fix them quickly with makeing snap shot and backing them up. Plus i can tinker and wont breaking anything else at the same time just resotre a snap shot and it back.

And share a printer for both Linux and Windows machines.

---

### Post by MilesTails on 2010-08-26
Sounds like what you need then is Samba for network file and print sharing

Community Ubuntu Docs for samba

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by barnesey on 2010-08-26
I have used samba on ubuntu server before, would it work the same if i set it up from the terminal?

---

### Post by MilesTails on 2010-08-26
It should. The configs and everything should remain the same as long as its the same version of Samba...ive done it from both server and desktop and havent noticed a difference anyway ;)

---

### Post by barnesey on 2010-08-26
:idea:, cool sounds good,

I will tell u all tomorrow how my TestDisk thing goes!!

---

### Post by barnesey on 2010-08-29
Test Disk dosent seem to have worked and all of my filesz that were in there isnt now!! So i am going to partion it to NTFS so i can make the windows shares etc.

Thanks Guys and thank you for reconmending parted magic it is much better than what i currently use for partitioning.

---

### Post by quixote on 2010-08-29
Aack.  WTH??  ???  Sounds like the only good news is that you didn't lose anything critical on that drive. :(

---

### Post by barnesey on 2010-08-29
There were a thing major thing lost but i am not worried about them atm. The stuff i tired to save was some backup files and images which i can make up again.

---

### Post by conradin on 2010-08-29
I had a bad super block a while back. you need to recover from an alternate block. Theres a link for a great tutorial in this thread!
[http://ubuntuforums.org/showthread.php?t=1245536&highlight=superblock](http://ubuntuforums.org/showthread.php?t=1245536&highlight=superblock)

---

### Post by barnesey on 2010-08-29
Its not worth worrying about it i have decided to take a chance and just format it, I can make up the images again other stuff, not really annoyed about,

I have formatted it to be NTFS so xubuntu and ubuntu can see it and i can share stuff with windows and linux computers.

Makeing the images up again so i have my backups al  up to date and organised.

---

