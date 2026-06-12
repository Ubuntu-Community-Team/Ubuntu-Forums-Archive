---
title: "New backup drive - which file system to use?"
date: 2012-07-05
forum: General Help
---

### Post by MarjaE on 2012-07-05
I picked up a new backup drive after a lot of trouble with my old one. I plan to format it and I'm wondering which file system would work best.

I want a file system which works smoothly with Linux, and can be checked and repaired from within Linux, and respects that not all file/directory names are Windows file/directory names.

I want a file system that I can read from and write to using Linux, Mac OS or Windows. I don't plan to use it to transfer files, but I might need to access it without being able to use Linux.

I don't want to run into permissions lock where I can't write to the  disk because, due to re-installation, it doesn't consider me the owner of that disk.

I have been using Back in Time as my backup software but other users here have suggested installing Deja Dup and using it instead.

Ext3 seems to be one of the more widely-suggested file systems, but I'm not sure how well it works with other operating systems or how easy to is to solve permissions problems.

So what would you suggest? Thanks.

---

### Post by msammels on 2012-07-05
Let me ask you this: do you plan on accessing this drive from other operating systems, such as Windows, or Mac OS X?

---

### Post by MarjaE on 2012-07-05
> **msammels said:**
> Let me ask you this: do you plan on accessing this drive from other operating systems, such as Windows, or Mac OS X?

Yes.

---

### Post by bab1 on 2012-07-05
> **MarjaE said:**
> Yes.

How do you want to do that?  Samba or...?  Maybe SFTP?

---

### Post by MarjaE on 2012-07-05
> **bab1 said:**
> How do you want to do that?  Samba or...?  Maybe SFTP?

I don't know what these things are. There's no real discussion of the issue in the only Linux manual I have [Ubuntu for non-Geeks, the version written for Lucid Lynx], and there's no mention of Samba or SFTP on the Wikipedia comparison:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

I just don't want the disasters I've had with NTFS, and I do want to be able to access this from other operating systems.

---

### Post by bab1 on 2012-07-05
> **MarjaE said:**
> I don't know what these things are. There's no real discussion of the issue in the only Linux manual I have [Ubuntu for non-Geeks, the version written for Lucid Lynx], and there's no mention of Samba or SFTP on the Wikipedia comparison:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

These are descriptions of local file systems.  The native file system for Linux is EXT and the current version is EXT4.  That is the best if you are using Ubuntu.

I just don't want the disasters I've had with NTFS, and I do want to be able to access this from other operating systems.
To access files and folders from other operating systems can mean 4 things.  You are either dual booting and have a partition that is native to Windows or ...?  Or you have a USB external drive that you use with both Ubuntu and Windows, or you are going to mount a remote file system to share files (Samba/Windows Shares) or you are going to transfer files to a remote machine (FTP).

So I'll ask again; how are you going to access these files?

---

### Post by Bucky Ball on 2012-07-05
Windows doesn't use Linux EXT filesystem at all. Not sure about Mac. NTFS should be fine for all. Not sure if Win can read Mac filesystem. (HFS?)

---

### Post by bab1 on 2012-07-05
> **Bucky Ball said:**
> Windows doesn't use Linux EXT filesystem at all. Not sure about Mac. NTFS should be fine for all. Not sure if Win can read Mac filesystem. (HFS?)
Sure Windows can read non-native file systems (FS).  If you are remote the local FS is irrelevant anyway.  Windows has a driver for EXT but you would not need it using either Samba or SFTP (or SSHFS).  There is a Windows driver for HFS too. 

But as I say, unless the foreign file system is locally mounted it doesn't matter.  The best FS is the one that is native to the local OS.

---

### Post by MarjaE on 2012-07-05
> **bab1 said:**
> To access files and folders from other operating systems can mean 4 things.  You are either dual booting and have a partition that is native to Windows or ...?  Or you have a USB external drive that you use with both Ubuntu and Windows, or you are going to mount a remote file system to share files (Samba/Windows Shares) or you are going to transfer files to a remote machine (FTP).

So I'll ask again; how are you going to access these files?

Okay.

First of all, I am dual booting, but I hardly ever use the Windows partition. Second, I used to use an older Mac and have been slowly migrating. It's been more than a year, but there are still a lot of files I need to convert over.

Third, NTFS has been a disaster because BackinTime stopped working, the Ubuntu disk utility can't handle NTFS and the Windows chkdsk can't handle certain file/directory names and certain file types.

Fourth, this is a backup drive, so it's by USB. I mean it could be by Firewire, I'm not sure what difference that would make. I've never had a network connection fast enough or reliable enough to try to back up over it.

---

### Post by bab1 on 2012-07-05
> **MarjaE said:**
> Okay.

First of all, I am dual booting, but I hardly ever use the Windows partition. Second, I used to use an older Mac and have been slowly migrating. It's been more than a year, but there are still a lot of files I need to convert over.

Third, NTFS has been a disaster because BackinTime stopped working, the Ubuntu disk utility can't handle NTFS and the Windows chkdsk can't handle certain file/directory names and certain file types.

Fourth, this is a backup drive, so it's by USB. I mean it could be by Firewire, I'm not sure what difference that would make.

So we are mounting the external drive via USB to the Linux OS (local).  And it appears you are going to backup the NTFS partition in a dual boot situation.  Additionally you may want to FTP some files from an old MAC that is also on the network.  Does this sound about right?

---

### Post by HermanAB on 2012-07-06
Well, unless you wish to install a foreign file system device driver on Windows, you are limited to NTFS.

---

### Post by MarjaE on 2012-07-06
> **bab1 said:**
> So we are mounting the external drive via USB to the Linux OS (local).  And it appears you are going to backup the NTFS partition in a dual boot situation.  Additionally you may want to FTP some files from an old MAC that is also on the network.  Does this sound about right?

Well, I'd like to back up the Windows user files, such as they are. I haven't been able to get file transfers to work. I basically copied everything from the Mac to a transfer disk and from the transfer disk to the current dual-booting machine. Then it's a matter of sorting through Mac-specific files [.cwk, .webarchive, etc.] to find which ones to try to convert and which ones to cut, and then back-and-forth runs with thumb drives.

In an emergency, if something goes wrong with this computer, I'd like to be able to access the backup disk from the Mac or from the Windows partition.

And no way am I using NTFS again.

---

### Post by bab1 on 2012-07-07
> **MarjaE said:**
> Well, I'd like to back up the Windows user files, such as they are. I haven't been able to get file transfers to work. I basically copied everything from the Mac to a transfer disk and from the transfer disk to the current dual-booting machine. Then it's a matter of sorting through Mac-specific files [.cwk, .webarchive, etc.] to find which ones to try to convert and which ones to cut, and then back-and-forth runs with thumb drives.

In an emergency, if something goes wrong with this computer, I'd like to be able to access the backup disk from the Mac or from the Windows partition.

And no way am I using NTFS again.
What do you mean by "transfer disk"?  Where on this "dual-booting machine" are you putting the data?  Is it on the external backup disk?  Are you running Ubuntu when you are moving the copies to the "dual-booting machine"?  Are you aware that your thumb drives are probably formatted WIN95/FAT32?

If you are going to move the external drive to a Windows or a Mac host you will need to for that drive to be able to interface with that host. 

Linux, Apple and Widows all read Win95/FAT (FAT32).  If you want to be able to move that external drive from host to host (or booting the original host into Windows) you will need to either have the filesystem drivers available (ntfs-3g, HFS, or EXT2/3/4) or a filesystem that is understood by all.  That would mean Win95/FAT (FAT32), just as your thumb drive does.  

The only other way to view the data is to do do that by manipulating  the data via an application like Samba or FTP, which you can install all of the OS's.  This means the data is hosted by one OS but can be viewed by all hosts as all the OS's have apps that understand Samba/Windows sharing or SFTP (SSH).

You need to decide which you want to do -- move the external disk around or run an application on each OS that can manipulate the the data from the host that the disk is mounted to.

I would choose the latter.  Use Ubuntu and format the external disk to EXT4.  Then backup the disks to this drive using an application like Filezilla (SFTP).  The if you wish you could share the data using Samba to the Mac and Windows hosts.

I don't have Apple machines in my network, but I do have Windows and Linux machines.  All my data is backed up to an external drive that I mount via a script and is formatted EXT4.  I can view the backups (rsync) using Samba.

---

### Post by MarjaE on 2012-07-07
> **bab1 said:**
> What do you mean by "transfer disk"?

A drive to put files on to move those files from one computer to another. I don't have a reliable enough network to do this any other way.

> Where on this "dual-booting machine" are you putting the data?Which data? The data for general use goes in the main Linux partition, the data for Windows goes in the Windows partition, and the backup goes on the backup drive.

> Is it on the external backup disk?The backup goes on the backup drive.

> Are you running Ubuntu when you are moving the copies to the "dual-booting machine"?  Are you aware that your thumb drives are probably formatted WIN95/FAT32?I'm using different operating systems on each end of the transfer. I'm running Ubuntu on the Linux end. And I haven't needed to shut down, boot into Windows, and run 21 hours of chkdsk on any of my thumb drives, so it's less of an issue than with a backup drive or a full-size transfer drive.

> If you are going to move the external drive to a Windows or a Mac host you will need to for that drive to be able to interface with that host. 

Linux, Apple and Widows all read Win95/FAT (FAT32).  If you want to be able to move that external drive from host to host (or booting the original host into Windows) you will need to either have the filesystem drivers available (ntfs-3g, HFS, or EXT2/3/4) or a filesystem that is understood by all.  That would mean Win95/FAT (FAT32), just as your thumb drive does.  

The only other way to view the data is to do do that by manipulating  the data via an application like Samba or FTP, which you can install all of the OS's.  This means the data is hosted by one OS but can be viewed by all hosts as all the OS's have apps that understand Samba/Windows sharing or SFTP (SSH).

You need to decide which you want to do -- move the external disk around or run an application on each OS that can manipulate the the data from the host that the disk is mounted to.

I would choose the latter.  Use Ubuntu and format the external disk to EXT4.  Then backup the disks to this drive using an application like Filezilla (SFTP).  The if you wish you could share the data using Samba to the Mac and Windows hosts.

I don't have Apple machines in my network, but I do have Windows and Linux machines.  All my data is backed up to an external drive that I mount via a script and is formatted EXT4.  I can view the backups (rsync) using Samba.

Well, the backup drive isn't supposed to be a transfer drive. But if anything happens to the Linux partitions [there is a failed installation of Xubuntu on another partition] I still want to be able to access the backup drive. So in an emergency, it has some of the same requirements as a transfer drive. And no reliable network.

---

### Post by bab1 on 2012-07-07
> **MarjaE said:**
> A drive to put files on to move those files from one computer to another. I don't have a reliable enough network to do this any other way.

Which data? The data for general use goes in the main Linux partition, the data for Windows goes in the Windows partition, and the backup goes on the backup drive.

The backup goes on the backup drive.

I'm using different operating systems on each end of the transfer. I'm running Ubuntu on the Linux end. And I haven't needed to shut down, boot into Windows, and run 21 hours of chkdsk on any of my thumb drives, so it's less of an issue than with a backup drive or a full-size transfer drive.

Well, the backup drive isn't supposed to be a transfer drive. But if anything happens to the Linux partitions [there is a failed installation of Xubuntu on another partition] I still want to be able to access the backup drive. So in an emergency, it has some of the same requirements as a transfer drive. And no reliable network.
So we don't have networked machines at all.  Just two physical machines, with one of them dual-booting.  This limits what we can do.  No Saamba, no SFTP etc.

Lets start with the backup disk.  Are you using this disk right now?  If so did you just plug it in and it works?  Where in the Linux filesystem do you see it?  Could it be at /media ?

[COLOR="Blue"]Edit:  I just came across you other thread regarding this same problem.  Since the eternal disk is formatted NTFS right now, you are getting a lesson about incompatibility of various file systems in use today. If you are going to use the drive with Linux use EXT.  If you want to mount it using Windows be prepared this type of frustration again.

If you want to move just the data between the two machines, network them and use a more modern method than a "sneaker net".  I move terabytes of data everyday with no problems in a Linux/Windows network using FTP and Samba.[/COLOR]

---

### Post by MarjaE on 2012-07-16
I can use NTFS, if I can find a Linux-based alternative to chkdsk. For whatever reason, the disk utility was unable to diagnose or repair the old hard drive, and I had to go into Windows to do that.

---

