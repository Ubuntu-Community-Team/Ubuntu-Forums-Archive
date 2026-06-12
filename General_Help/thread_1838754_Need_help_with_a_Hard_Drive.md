---
title: "Need help with a Hard Drive"
date: 2011-09-04
forum: General Help
---

### Post by aviator1 on 2011-09-04
I installed a second HD, and all was well until I used the "dd" command to clone the first HD to the second. 

The first HD was my dual boot 320GB and the new one was a new/blank 2TB. My intention was to get Linux on the new one without having to rebuild all my favorites and save emails, etc.

I followed the instructions on another thread here about using "dd" but I am not doing well.

I would appreciate any help. I have been using Linux for a year, but I am not a programmer type, just a user.

I assume I need to erase/format the new HD to get back to square 1.

BTW, before using "dd" I did have Ubuntu 10.04 on the new drive and it was booting and operating normally. 
Now if I have only the new HD connected, it will not boot. Just locks.

Thanks for any help.

Dave

---

### Post by Basher101 on 2011-09-04
Question one: How big is your installation WITHOUT documents,music,downloads, every bit of movable data?
If you are below 18GB then it will be very easy. Just move everything you can move out of your installation. Then you will be able to make a bootable Live .iso of your ***current*** installation with all settings and programs. Just try to get to 18 GB

---

### Post by aviator1 on 2011-09-04
Thanks for your reply.

The short answer is I don't know. My original HD is a 320GB unit, and has about 1 GB left. I have Vista and Ubuntu 10.04 on it as well as various other programs.

I do not particularly want Vista on the new 2TB drive, only Linux.

---

### Post by Basher101 on 2011-09-04
the program will only make a bootable live .iso from your ubuntu install, nothing else. Just try to make it as small as possible and move all your data (movies,music,documents, downloads) somewhere else. The program that will do that for you is called Remastersys, but it has some space limitations (it comprimises space, but the bootable .iso must NOT be bigger than 4 gb, so if you try to make a bootable iso with more than 18gb it will very likeley not work). Otherwise its the easiest backup program you can use, your live .iso can be burnt to DVDs or you can make a bootable Live USB and have your whole system on it. Just try to minimize space and your as good as done.

---

### Post by aviator1 on 2011-09-04
Thanks again for the quick reply.

The problem is for now, I cannot do anything with the new HD. 

I would like to get to a "start over" point where I can use remastersys.

Any suggestions on how to erase/reformat the new HD so I can start over?

---

### Post by Basher101 on 2011-09-04
over what port is it connected? is it an internal Hard drive? or external? you can use Gparted to reformat it completeley.

---

### Post by aviator1 on 2011-09-04
Both drives are internal drives. Do not know where to find what port it is on. I do not have gparted that I know of.

Thank you for your answers.

---

### Post by Basher101 on 2011-09-04
Gparted is in the repos. Just open the software centre and search Gparted and install it. Be careful that you know exactly what you are doing as you can format partitions that you do not want to. If you installed it i would gladly apply with screenshots to guide you.

---

### Post by aviator1 on 2011-09-04
I have gparted and just used it to look at the new drive. I got some warnings "Failed to start up", "failed to mount", "invalid argument"

However, I cannot seem to copy the warnings to show you.

I am able to look at the contents of the new drive, and everything seems to have been copied there.

My goal is to used the new drive as only Linux, and be able to save my previous emails, and favorites.

I really appreciate your help.

---

### Post by aviator1 on 2011-09-04
Sorry. Have to leave for a few hours.

Any help is appreciated.

Dave

---

### Post by aviator1 on 2011-09-04
Hello All:

I posted earlier, but have dug a deeper hole for myself and just decided to throw away the shovel. 

Here's the tale of woe.......

My existing internal 320GB HD was getting full, so I purchased a new 2TB internal HD.

I installed the 2TB, and successfully installed Ubuntu 10.04.

However, being lazy and not wanting to rebuild favorites, plus wanting to save emails, I decided to try to copy from my existing disk to the new disk. I searched these forums and found someone touting the use of the "dd" command. I looked good, but screwed up access to the new disk.

I used gparted to reformat the new disk, and now viewing places\computer browser, the new drive is not found.

I have the case open, so I switched ata cables and tried to boot off a cd....no luck...boot process just stops.

I have been using 10.04 since last October, but am not well versed on commands using terminal, so any suggestions in that direction need to be spelled out very well. Been married 38 years. I can follow instructions :-)

---

### Post by drs305 on 2011-09-04
Threads merged. Please only create one thread per issue and allow users time to respond. If additional information is needed or becomes available, just create a new post in the original (this) thread.

---

### Post by oldfred on 2011-09-04
Do you have both drives connected? After using dd you copy everything including the UUIDs that have to be unique. 

See what this says.

sudo blkid

---

### Post by papibe on 2011-09-04
A few thoughts,

Even if you switch data cables. the boot order may be set in the BIOS to the specific HD is (like brand name). Check your BIOS to make sure the system boots to hard drive you want.

Nowadays, most mount tables (/etc/fstab) are hardcoded to disks ids instead of devices. That means that even if you boot in the correct drive, it may be necessary to make changes on fstab to get all working as you want.

To update your fstab you'll need to boot into the safe mode (or use the LIVE CD in the worst case) and use this command to get your UUIDs:
```
$ sudo blkid
```

For more information take a look at this help page: [Introduction to fstab]("https://help.ubuntu.com/community/Fstab").

Hope it helps,
Regards.

---

### Post by aviator1 on 2011-09-04
Here is what sudo blkid says:

[sudo] password for dave: 
/dev/loop0: UUID="9033f6b8-4957-425b-99e2-ed6b706fbc04" TYPE="ext4" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-090E" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="C002006A020067AC" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="36A20437A203F9DF" TYPE="ntfs" 
dave@ubuntu:~$

---

### Post by aviator1 on 2011-09-04
The original setup was 320GB as a dual boot vista/ubuntu and the second disk was a 75Gb storage. I placed the 320GB in the #2 position and installed the 2TB new disk in the number 1 position. Booted with Ubuntu cd and installed ubuntu on the new 2 TB OK. Tried the "dd" deal and things went downhill. Will be out a copule of hours, but any help is appreciates. Here is what sudo blkid says:
[sudo] password for dave: 
/dev/loop0: UUID="9033f6b8-4957-425b-99e2-ed6b706fbc04" TYPE="ext4" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-090E" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="C002006A020067AC" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="36A20437A203F9DF" TYPE="ntfs" 
dave@ubuntu:~$

---

### Post by papibe on 2011-09-04
Is that a Wubi install?

---

### Post by aviator1 on 2011-09-04
On the 320GB it was a wubi install. On the new 2TB drive, it was off a downloaded ubuntu cd

---

### Post by aviator1 on 2011-09-04
My goal is to have only Ubuntu on both drives. No Vista. It would not matter to be if the 320GB stayed the primary and the 2TB became a backup/storage drive.

I just can't seem to see the second drive except with gparted.

Thanks for any help.

Dave

---

### Post by YesWeCan on 2011-09-04
Exactly what dd command did you use?

---

### Post by aviator1 on 2011-09-05
[I]dd if=/dev/sda of=/dev/sdb

I'll try to find the thread whee I got that from.
[/I]

---

### Post by YesWeCan on 2011-09-05
Ok. Make sure you disconnect the original drive or neither will boot properly. This is because the boot loaders and file system mounters will get confused by duplicate partition identifiers.

Then boot live CD and download and run this [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and post RESULTS.txt here in code tags (highlight text and click # above) so we can see what is going on.
:)

---

### Post by pratikk on 2011-09-05
Just a thought, since gparted can see the drive but the system can't -- or that's the impression I got. Did you format the 2TB to a filesystem, or did you only delete it? Was it an ext filesystem?


Sorry, I misunderstood an earlier post

---

### Post by aviator1 on 2011-09-05
@ YesWeCan.....Will do and will post. Have to be out for a few hours

---

### Post by aviator1 on 2011-09-05
> **pratikk said:**
> Just a thought, since gparted can see the drive but the system can't -- or that's the impression I got. Did you format the 2TB to a filesystem, or did you only delete it? Was it an ext filesystem?


Sorry, I misunderstood an earlier post

Yes, I formatted the 2TB drive using gparted. Advice from another thread.

Do not understand the terms "to a filesystem" or "ext filesystem"

In gparted, I used "device" and erase everything.

---

### Post by oldfred on 2011-09-05
You have to create partitions and format them as a file system. NTFS for windows and ext2, ext3 or ext4 for Linux among many other formats.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by aviator1 on 2011-09-05
> **oldfred said:**
> You have to create partitions and format them as a file system. NTFS for windows and ext2, ext3 or ext4 for Linux among many other formats.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


I have made some progress. I used gparted to partition the 2TB drive. I have a 800GB primary as an ext3, a 600gb as an ext3, a 200gb as an nfts, and the remainder as unallocated.

I now see the drives/partitions when I look at "Places" on my menu bar.

However, I tried to boot with my cd and having only the 2TB connected. No dice.

I tried to boot with my cd with the 2TB as primary and the 320gb as secondary. No dice.

I tried to copy the cd to the primary partition. No dice.

What is my next step to get Ubuntu 10.04 on the 2TB drive?

Thanks to all for the help received. 

Dave

---

### Post by aviator1 on 2011-09-05
Much more success!

After partitioning the 2TB drive, I found that my live cd was bad.

Got another one, booted up and installed 10.04 successfully.

However, in trying to boot to my original 320 drive, I get a grub boot error. I will tackle that next as another thread.

I thank all of you who took the time to guide me in the right direction.

Regards, 

Dave[IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

---

