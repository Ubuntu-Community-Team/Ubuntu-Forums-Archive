---
title: "Folder Visible in Ubuntu 10.4 not in Win 7"
date: 2010-09-13
forum: General Help
---

### Post by nhutto on 2010-09-13
Ok so I have a folder on a fat32 partition that is mounted in both os's on my system.(Ubuntu 10.4 and Win 7) When I go to windows 7 the partion is mounted but I can not find the Music Folder on the drive. When i have it booted in linux I have access to the Music folder. The last change on my system I made was I ran edna-0.6 for a day so I could stream the contents of the folder. I need to figure out how to get access to these in windows again. Any Ideas welcome

//output from ls-l on my /media/osShare mount
total 544
-rwxrwx---   1 root plugdev      0 2010-09-08 21:32 admins.txt
-rwxrwx---   1 root plugdev      0 2010-09-08 21:32 banned-ip.txt
-rwxrwx---   1 root plugdev      0 2010-09-08 21:32 banned.txt
drwxrwx---   8 root plugdev  16384 2009-06-06 01:57 Dads backup
-rwxrwx---   1 root plugdev     75 2010-09-08 21:59 externalurl.txt
drwxrwx---   5 root plugdev  16384 2009-06-01 03:07 FSCK0000.000
drwxrwx---   6 root plugdev  16384 2009-02-18 08:27 home
-rwxrwx---   1 root plugdev  63748 2009-12-11 15:20 minecraft-server.jar
drwxrwx---   2 root plugdev  16384 2010-07-10 03:11 msdownld.tmp
drwxrwx--- 303 root plugdev  32768 2010-09-12 21:59 Music
drwxrwx---   5 root plugdev  16384 2009-07-29 07:09 Nhutto
drwxrwx---   4 root plugdev  16384 2009-08-28 22:03 Pictures
-rwxrwx---   1 root plugdev      0 2010-09-08 21:59 players.txt
-rwxrwx---   1 root plugdev   3861 2009-12-11 15:19 README.TXT
drwxrwx---   2 root plugdev  16384 2010-09-11 00:31 $RECYCLE.BIN
drwxrwx---   2 root plugdev  16384 2009-05-21 21:20 Recycled
-rwxrwx---   1 root plugdev 196948 2010-09-08 22:03 server_level.dat
-rwxrwx---   1 root plugdev   1188 2010-09-08 22:04 server.log
-rwxrwx---   1 root plugdev    258 2010-09-08 22:04 server.properties
-rwxrwx---   1 root plugdev    162 2010-09-08 21:32 start server.bat
drwxrwx---   4 root plugdev  16384 2009-02-14 15:08 System Volume Information
drwxrwx---   4 root plugdev  16384 2009-05-19 10:54 Videos

---

### Post by wilee-nilee on 2010-09-13
Have you ever seen the folders from W7, are you running a different bit type for either OS, ie 32 vs 64 bit. It looks as though your saying get back what you could originally see in W7 is this correct.

---

### Post by nhutto on 2010-09-13
Yeah I had all these files last night. and both OS's are 64. I think it has to be a setting but I can't seem to find anything to solve this. I will post what ever will help with making it visible.

---

### Post by wilee-nilee on 2010-09-13
> **nhutto said:**
> Yeah I had all these files last night. and both OS's are 64. I think it has to be a setting but I can't seem to find anything to solve this. I will post what ever will help with making it visible.

I would take a look at the partition and windows from gparted to see if there are any flags, you might just need a chkdsk of sorts, when you let Ubuntu read and write to a shared partion=ie edna you might have messed with the partition enough that Windows log files are not working correctly. I am assuming here, but I found some anomalies in my W7 setup when I removed a release ISO from a shared ntfs from Ubuntu. Reset itself when I rebooted W7 though.

I am assuming you are familiar with running a chkdsk and what commands to use.

---

### Post by nhutto on 2010-09-14
for a temp solution I created a new folder and am in the process of transferring the files through ftp to make sure no permissions are there anymore. and once that is done I will run a chkdsk.

And the gparted has no flags for that partition.

---

### Post by nhutto on 2010-09-16
This just gets better. So The following day i got home from work and the files were there this time ... in win 7 ... then the following night nope both days I ran edna in linux ... ran chkdsk on drive and said it did not have enough space to fix the drive... drive under half full... said it only had 2.5 gigs of space actually has 104 gigs. wtf any ideas once again welcome.

---

### Post by Mark Phelps on 2010-09-16
Been a while since I've seen that error message, but from my own experience, it meant that the MFT had become corrupted.  Trying to run chkdsk appeared to have no positive results.

You know, these are the "Ubuntu forums", not the Windows 7 forums.  A bunch of us here also use Win7 -- but we're not the established experts.

My recommendation is that you post your concerns to the premier Win7 forum -- sevenforums.com.  Perhaps the experts there can tell you how to clean up your partition to fix this problem.

---

### Post by coffeecat on 2010-09-16
Following on from what Mark Phelps said about MFT corruption, you might find it quicker and less of a hassle in the long run to back up all your files onto another medium and reformat the partition. If you do that, have a think about using NTFS rather than FAT32 for a shared partition between Ubuntu and Windows 7. NTFS is more robust than FAT32, read-writing NTFS is reliable enough in Ubuntu and you have Windows to chkdsk it if anything goes wrong.

---

### Post by Mark Phelps on 2010-09-16
While I agree with coffeecat regarding his advice, I still recommend posting to sevenforums.com.

Why?

Because Win7 has introduced new diagnostic utilities -- with which I'm not personally familiar -- and you may be able to use them to diagnose and fix your MFT problem.

---

