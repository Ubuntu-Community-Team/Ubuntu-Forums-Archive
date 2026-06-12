---
title: "which filesystem is most stable?"
date: 2010-04-02
forum: General Help
---

### Post by 37fleetwood on 2010-04-02
I had a recent scare where a 1 terabyte Western Digital "My Book" was halfway unplugged and when I rebooted the computer it scrambled the drive a bit. I got it sorted out, but now I'm wondering which filesystem is the most stable and reliable.
here's what I have and need, I have a dual core 64 bit processor and 4 gig of ram. I am running the 64 bit version of Ubuntu 9.10 on ext4 and Windows XP64 on ntfs as a dual boot. the drive as mentioned is a 1tb western Digital USB "My Book". currently it is formatted ext3. I have been accessing it with Windows using a ext3 driver. at the time this seemed to be the easiest way since Ubuntu didn't seem willing to automatically mount the drive when it was FAT32.
my concern is, sometimes things get unplugged, sometimes the power goes out, and Ubuntu doesn't like that very much.
with Windows you just reboot and if it feels like it, it will go through chkdsk and then boot, with Ubuntu I've had it refuse to boot until I boot to the live disk and use G Parted to check the drives.
this last issue wouldn't have been so easily solved if I hadn't had Windows. Ubuntu refused to mount the drive, and Windows let me. I moved all the important stuff off the drive and then fixed the error.

so my question now is which filesystem is best to use for a largish storage drive?
the important considerations are:
easy access by Linux, and Windows
overall reliability/durability
access speed
would it be wise to split the drive into two 500gig partitions, one ntfs, one ext3.

---

### Post by prodigy_ on 2010-04-02
In short: **NO** filesystem is safe, stable and reliable when it's exposed to power failures.

Don't rely too much on tools like chkdsk and fsck. Have an up-to-date backup and you won't have a reason to worry.

---

### Post by kokkus on 2010-04-02
Ubuntu Lynx 10.04 will be the best solution for you.
This version is a LTS version (long time support) which means they are focusing on stability and stuff.
Also, to mount drivers automatically you can install a little package called pysdm. Use root permission (sudo).

---

### Post by humanaut on 2010-04-03
XFS is a very mature filesystem that handles large data & large data transfers very well.

---

### Post by lovinglinux on 2010-04-03
> **kokkus said:**
> Ubuntu Lynx 10.04 will be the best solution for you.
This version is a LTS version (long time support) which means they are focusing on stability and stuff.
Also, to mount drivers automatically you can install a little package called pysdm. Use root permission (sudo).

Please keep in mind Lucid is still Beta and not recommended for production environment.

> **prodigy_ said:**
> In short: **NO** filesystem is safe, stable and reliable when it's exposed to power failures.

Don't rely too much on tools like chkdsk and fsck. Have an up-to-date backup and you won't have a reason to worry.

I have been using ext4 since Jaunty and it is very stable for me. I have experienced several power outages (15 since November) and never had a problem with data loss, except for some torrents that were missing pieces despite being considered completed by Ktorrent. These torrents were running during the power outage and weren't complete at that time.

Anyway, I don't think Windows will be able to read ext4.

---

### Post by 37fleetwood on 2010-04-03
seems there is no support for xfs available for Windows. if the post above is correct I should be able to format it to ntfs and convince Ubuntu to play nice with that using pysdm if I can figure it out, I'm not very familiar with the command line. when I got the "My Book", it was formatted FAT32, I could go back to that.

---

### Post by nem75 on 2010-04-03
> **lovinglinux said:**
> Anyway, I don't think Windows will be able to read ext4.

True, but using VirtualBox there are quite elegant [ways around that]("http://ubuntuforums.org/showthread.php?p=7872120").

---

### Post by coffeecat on 2010-04-03
> **37fleetwood said:**
> seems there is no support for xfs available for Windows. if the post above is correct I should be able to format it to ntfs and convince Ubuntu to play nice with that using pysdm if I can figure it out, I'm not very familiar with the command line. when I got the "My Book", it was formatted FAT32, I could go back to that.

You don't have to convince Ubuntu to play nice with NTFS. NTFS read-write works out of the box in Ubuntu, and NTFS external drives are automounted when you plug them into Ubuntu. I agree with the poster who said that no filesystem is reliable in the event of a power failure, but the advantage of NTFS over FAT32 is that it is journalled and can (often) be repaired with Windows chkdsk. And I agree that you need to rely on backups - not the relative merits of your chosen filesystem

Curious that you had problems with FAT32 on your MyBook. FAT32 should be trouble-free in Ubuntu. Anyway - I use NTFS on most of my external drives, mainly because (with ntfs-3g on my Mac) that's the best compromise for using with Ubuntu, Windows and MacOS. I have yet to have a significant problem.

---

### Post by 37fleetwood on 2010-04-03
> **coffeecat said:**
> You don't have to convince Ubuntu to play nice with NTFS. NTFS read-write works out of the box in Ubuntu, and NTFS external drives are automounted when you plug them into Ubuntu. I agree with the poster who said that no filesystem is reliable in the event of a power failure, but the advantage of NTFS over FAT32 is that it is journalled and can (often) be repaired with Windows chkdsk. And I agree that you need to rely on backups - not the relative merits of your chosen filesystem

Curious that you had problems with FAT32 on your MyBook. FAT32 should be trouble-free in Ubuntu. Anyway - I use NTFS on most of my external drives, mainly because (with ntfs-3g on my Mac) that's the best compromise for using with Ubuntu, Windows and MacOS. I have yet to have a significant problem.
please let me clarify, when I go to access my Windows partition it asks me for the administrator password every time, I would like this drive to mount automatically when I boot the computer. also I typically leave this drive plugged in all the time.
I didn't mean to give the impression I had trouble with FAT32, the decision to go with ext3 was purely a ease of use issue.

here's what I want, I want to boot to Windows and have the mybook accessible as if it were a regular drive, I also want to be able to boot to Ubuntu and have the mybook accessible as if it were a regular drive. I want to be able to do this as safely as possible.
I'm guessing backing up a 1tb drive is going to be problematic in several ways, there is nothing I can't lose on the drive but lots of stuff I would rather not lose, my truly critical stuff is backed up.

---

### Post by coffeecat on 2010-04-04
> **37fleetwood said:**
> please let me clarify, when I go to access my Windows partition it asks me for the administrator password every time, I would like this drive to mount automatically when I boot the computer. also I typically leave this drive plugged in all the time.

Clarify? :p In fact that sentence is ambiguous. When I first read it I thought the "I would like this drive to mount automatically" referred to the Windows partition. Anyway, I think I get your drift now.

If I do understand you correctly, the solution is simple. But first:

Mounting internal partition: clicking on a partition listed in Places and then being prompted for your password is normal behaviour. If you want it mounted at bootup, you add a line to /etc/fstab.

Mounting external drive: If you plug one into a running desktop it gets mounted automatically without you having to enter a password - but you know that already.

However - **and I think this is the bit that helps you** - if the USB drive is plugged in and powered up before you boot up, it'll be mounted automatically during bootup with a clickable icon on the desktop. This is true of NTFS, FAT32 and ext3/4 formatted drives, although with ext3/4 being mounted by root you'll have to do some chown-ing to be able to use it as an ordinary user. (In fact, NTFS and FAT32 drives are mounted by root, but you can access them as an ordinary user since MS filesystems don't support Linux permissions.)

If you want to mount the external drive to a specific mountpoint, then you need to add an appropriate line to /etc/fstab. If it's automounted, a mountpoint is created for you, with a name following certain rules. I always apply partition labels when I format the drive, and the system uses the partition label as the mountpoint name. For instance, I just tried booting into Karmic with a 60GB Seagate drive formatted NTFS plugged in. The partition label is "Seagate60NTFS". After I logged in, an icon labelled "Seagate60NTFS" was sitting on my desktop.

Which leads us back to the filesystem you need. In your situation, my preference would be for NTFS. You are limited by your need to accommodate Windows. And, as others have stated, no filesystem is 100% reliable. If you are going to suffer power cuts and/or unclean unmounts then you may experience data loss. At least NTFS is more robust than FAT32.

---

### Post by 37fleetwood on 2010-09-27
it's been a while which was intentional as I wanted to gain time using the different systems. here is what I have found.
if you are using a dual boot system because there is a reason you still need Windows there will likely be a time when you need to access files between the two, which means trying to get files from an NTFS or FAT file system from Linux, or trying to access a Linux file system from Windows.
the issues I have found are these:
1. accessing a large NTFS filesystem from Linux is very slow. whether it's a product of the filesystem or the drivers or both I don't know but take my word for it, an Ext partition is about twice or more faster to access.
2. accessing an Ext2 or Ext3 partition requires a driver which requires an application to run it and is sketchy at best. I haven't found a driver that will let you access an Ext4 partition from Windows.

This led me to the conclusion of using an intermediary drive. my original question was which partition type would be best to use to store things I might need access to from either Windows or Linux. I tried Ext3 for a while and have been trying NTFS for a while now. the obvious conclusions are that to use Ext3 in windows requires the driver program which is a hassle but once it is set up it does work, and using NTFS works well with both operating systems but is terribly slow and causes more trouble if you have a power outage. both systems work, I'm leaning toward Ext3 because of the speed issue.

---

