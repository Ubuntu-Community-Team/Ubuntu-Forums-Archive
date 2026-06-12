---
title: "Disk Usage Analyzer error"
date: 2009-12-31
forum: General Help
---

### Post by suniyo on 2009-12-31
I receive a pop-up notice with a warning that I am running low on disk space something around 400mb but when I actually check it with the Disk Usage Analyzer it is around 2GB free at the moment. Where is the error? In the Disk Usage Analyzer or in the pop-up error message.

Few days back my Transmission  bittorrent client crashed when my monitor was locked in power saving mode and I turned the ubuntu machine off directly from AC mains power supply. I lost 1.5 GB worth of downloaded data than. 

Is this that missing data from the bittorrent client that is not shown in the Disk Usage Analyzer when I run to check it, if so where is that data stored so that I can delete it manually. (Basically music and few softwares I downloaded)

Or I am missing something and error is somewhere else.

---

### Post by suniyo on 2009-12-31
After a bit of research I cann't find any relationship between Disk Usage Analyzer and Transmission bittorrent client. So where is the error?

---

### Post by suniyo on 2009-12-31
is there anyone out there who can help me with this. running really low on resources now!!

---

### Post by iWolf on 2009-12-31
There might be an error in your Disk Analyzer, your better off finding that package and re-installing it, that's the only thing I can say. Just look for the packages on google, re-install them and check it out.

Cheers!
iWolf

---

### Post by suniyo on 2009-12-31
> **iWolf said:**
> There might be an error in your Disk Analyzer, your better off finding that package and re-installing it, that's the only thing I can say. Just look for the packages on google, re-install them and check it out.

Cheers!
iWolf

I have reinstalled it once and I think there is some error due to power failure but where? I don't know exactly.

---

### Post by SecretCode on 2009-12-31
How big is the disk? What is its filesystem - ext3/ext4/...?

You can get a disk space warning when a prog tries to allocate a few hundred MB, then it gives up and frees the space. Or some other process frees up temporary files. You might find both tools are correct!

I don't know anything about that bittorrent client. I would believe Disk Usage Analyser first.

---

### Post by dcstar on 2009-12-31
> **suniyo said:**
> I receive a pop-up notice with a warning that I am running low on disk space something around 400mb but when I actually check it with the Disk Usage Analyzer it is around 2GB free at the moment. Where is the error? In the Disk Usage Analyzer or in the pop-up error message.

Few days back my Transmission  bittorrent client crashed when my monitor was locked in power saving mode and I turned the ubuntu machine off directly from AC mains power supply. I lost 1.5 GB worth of downloaded data than. 

Is this that missing data from the bittorrent client that is not shown in the Disk Usage Analyzer when I run to check it, if so where is that data stored so that I can delete it manually. (Basically music and few softwares I downloaded)

Or I am missing something and error is somewhere else.
User run tools do not show files that the user has no rights to see:
```
gksudo baobab
```

---

### Post by suniyo on 2009-12-31
> **dcstar said:**
> User run tools do not show files that the user has no rights to see:
```
gksudo baobab
```


I will give it a try but I think my user account has all superuser privileges. Let me check it in terminal.

---

### Post by suniyo on 2009-12-31
> **SecretCode said:**
> How big is the disk? What is its filesystem - ext3/ext4/...?

You can get a disk space warning when a prog tries to allocate a few hundred MB, then it gives up and frees the space. Or some other process frees up temporary files. You might find both tools are correct!

I don't know anything about that bittorrent client. I would believe Disk Usage Analyser first.

It is an ext4 partition.  An image of palimpsest disk utility result is attached with this post to have a complete look at my file system.

---

### Post by xifer on 2009-12-31
> **suniyo said:**
> I receive a pop-up notice with a warning that I am running low on disk space something around 400mb but when I actually check it with the Disk Usage Analyzer it is around 2GB free at the moment. Where is the error? In the Disk Usage Analyzer or in the pop-up error message.

Few days back my Transmission  bittorrent client crashed when my monitor was locked in power saving mode and I turned the ubuntu machine off directly from AC mains power supply. I lost 1.5 GB worth of downloaded data than. 

Is this that missing data from the bittorrent client that is not shown in the Disk Usage Analyzer when I run to check it, if so where is that data stored so that I can delete it manually. (Basically music and few softwares I downloaded)
.

some bt clients reserve the disk space before starting the download, I wouldn't expect a crash to lose any data though.  Did you manually delete all the torrents plus data after the crash?  If not then try it - if the torrents are not currently open in bt then open them from bt and make sure the data is deleted (reserved space is freed).

---

### Post by suniyo on 2009-12-31
> **xifer said:**
> some bt clients reserve the disk space before starting the download, I wouldn't expect a crash to lose any data though.  Did you manually delete all the torrents plus data after the crash?  If not then try it - if the torrents are not currently open in bt then open them from bt and make sure the data is deleted (reserved space is freed).

It is not like that. What actually happened:

My monitor LG Flatron2043T went into the powersaver mode when I switched it off and put away while Transmission bittorrent client downloading some music+software+movies. When I turned the monitor on it never came out of the powersaver mode so I directly switched off the computer. now when computer was restarted again all torrents loaded into the TB Client started verifying data on disk (obvious because of unclean shutdown) and downloads were actually gone. It actually should have downloaded 1.5 GB but it showed something around 10MB. So something is wrong with the TB client and data is somewhere on my disk though it is not shown actually in torrent client.

---

### Post by SecretCode on 2009-12-31
> **dcstar said:**
> User run tools do not show files that the user has no rights to see:
```
gksudo baobab
```

Not perfect ... if I run this, it does not see my ~/.VirtualBox folder (which has 13.5GB in it!) - or a bunch of others. Why would that be?

---

### Post by suniyo on 2009-12-31
> **dcstar said:**
> User run tools do not show files that the user has no rights to see:
```
gksudo baobab
```

I have tried this it doesn't make any difference. Torrents were actually removed from the client but data was not deleted and it is somewhere on my disk but where? It doesn't show up in filesystem anywhere.

---

### Post by dcstar on 2009-12-31
> **SecretCode said:**
> Not perfect ... if I run this, it does not see my ~/.VirtualBox folder (which has 13.5GB in it!) - or a bunch of others. Why would that be?

Because these folders/files have no System read rights.

---

### Post by SecretCode on 2009-12-31
suniyo: try the following:
```
sudo du -x --max-depth 1 /
```
The last line is the total usage. 

Also do the same without sudo ... just in case.

> **suniyo said:**
> So something is wrong with the TB client and data is somewhere on my disk though it is not shown actually in torrent client.
Do you want to recover it or just delete it?

Assuming it stored the partial download as a single file, not a lot of small chunks, try
```
sudo find / -mount -size +1G
```
You can try other values instead of +1G ... +100M, etc

---

### Post by suniyo on 2009-12-31
> **dcstar said:**
> Because these folders/files have no System read rights.

[http://ubuntuforums.org/showthread.php?p=8586892#post8586892](http://ubuntuforums.org/showthread.php?p=8586892#post8586892) << check the attachment.

---

### Post by SecretCode on 2009-12-31
> **dcstar said:**
> Because these folders/files have no System read rights.

"But they do" I was thinking ... but in fact only ./VirtualBox is drwxr-xr-x; all the files are -rw-------. Thanks

---

### Post by suniyo on 2009-12-31
> **SecretCode said:**
> suniyo: try the following:
```
sudo du -x --max-depth 1 /
```The last line is the total usage. 

Also do the same without sudo ... just in case.


Do you want to recover it or just delete it?

Assuming it stored the partial download as a single file, not a lot of small chunks, try
```
sudo find / -mount -size +1G
```You can try other values instead of +1G ... +100M, etc

I just want to delete them as already downloaded files again and have a copy of them on a DVD.

I think ```
sudo find / -mount -size +1G
``` is not going to help as if it is raw torrent data piece are 1mb or 512 kb in size.

What this command actually does:```
 sudo du -x --max-depth 1 /
```

---

### Post by geirha on 2009-12-31
> **suniyo said:**
> I just want to delete them as already downloaded files again and have a copy of them on a DVD.

I think ```
sudo find / -mount -size +1G
``` is not going to help as if it is raw torrent data piece are 1mb or 512 kb in size.


What release of Ubuntu or version of the Bittorrent client (Usually shown from the apps Help menu -> About ...) you are using? Did you force a recheck of torrent data? 

> **suniyo said:**
> 
What this command actually does:```
 sudo du -x --max-depth 1 /
```

du is a command-line tool to see disk usage.
The -x option makes it stick to one filesystem (E.g. not descend into windows drives mounted in /media etc.)
--max-depth 1 means it should only list one (the first) level of directories in the tree (the default is to recurse all the way to the leaf nodes, which will produce a lot more output than needed)
/ is the directory to look at.
You can confirm all this by reading du's man-page by typing in a terminal:
```
man du
```

I usually filter it through sort, so that the directories with most used space are listed at the bottom.
```
sudo du -x --max-depth=1 / | sort -n
``` Sizes are listed in KiBs btw.

Also, what's the output of this command? ```
df -h /
```

---

### Post by suniyo on 2009-12-31
> **geirha said:**
> 

Also, what's the output of this command? ```
df -h /
```

Output of the command is show here which is in direct conflict with the output of the disk usage analyzer results:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              30G   26G  2.4G  92% /

disk usage analyzer says i have 3.8 GB free space, have attached an image of the DUA for reference.

---

### Post by suniyo on 2009-12-31
> **geirha said:**
> What release of Ubuntu or version of the Bittorrent client (Usually shown from the apps Help menu -> About ...) you are using? Did you force a recheck of torrent data? 


Ubuntu: 9.10 Karmic Koala. 
TB Client: Transmission 1.75 (9117)

---

### Post by xifer on 2009-12-31
If you still haven't identified anything from the info above then maybe quit to single user mode and run fsck.

---

### Post by suniyo on 2009-12-31
> **xifer said:**
> If you still haven't identified anything from the info above then maybe quit to single user mode and run fsck.

 I am not getting it what exactly you want to say.

---

### Post by xifer on 2009-12-31
boot into recovery mode and run fsck - check the disk for errors.

ctrl-alt-F1 - log in as root

init 1

or choose the option from the boot menu

---

### Post by suniyo on 2009-12-31
> **xifer said:**
> boot into recovery mode and run fsck - check the disk for errors.

ctrl-alt-F1 - log in as root

init 1

or choose the option from the boot menu

If I have some errors on disk after checking with fsck what do I need to do? Should correct it there in recovery mode? Am I going to lose any data after during or after the operation of filesystem repair. It is important to me because I have no backups right now.

---

### Post by SecretCode on 2009-12-31
Having DUA not see all the data could be understandable (due to permissions), but the 'available space' it reports should come from the drive not from its calculations. I'm not sure why it is giving a different result from *df*.

I think running fsck is a good idea. It will correct errors itself, and the only data you will lose is data that's not linked into the filesystem properly - so is already 'lost'.

---

### Post by xifer on 2009-12-31
actually the best way to run this might be

```

su -
cd /
touch /forcefsck
reboot

```

You're unlikely to lose anything bad but will be prompted to repair or not if errors are found. Say no at first if you like and see how things look.

---

### Post by suniyo on 2009-12-31
> **SecretCode said:**
> Having DUA not see all the data could be understandable (due to permissions), but the 'available space' it reports should come from the drive not from its calculations. I'm not sure why it is giving a different result from *df*.

I think running fsck is a good idea. It will correct errors itself, and the only data you will lose is data that's not linked into the filesystem properly - so is already 'lost'.

But what if there is say a bug in Transmission bittorrent client? I may lose lot of transfers worth almost 4GB and it is pain to download them again at 512kbps connection. :(

---

### Post by rnerwein on 2009-12-31
high - i think it's enough - just open a terminal and run followin command as super user (root).
tune2fs -l /dev/your_device and you will see all about your filesystem. look at the parameter
Reserved block count:     1228771 . this is the default when the filesystem was created. your filesystem is 32gb and 5% are ~ 2gb. the reservation is for processes running with root account (eg. daemons).
the 5% are are history. today we have filesystems with 1terra or more !!!!. 
use tune2fs to change your reserved-block size, but please don't set it to zero - (200 mb should be enough). i hope this will help. ciao richi

---

### Post by suniyo on 2009-12-31
> **rnerwein said:**
> high - i think it's enough - just open a terminal and run followin command as super user (root).
tune2fs -l /dev/your_device and you will see all about your filesystem. look at the parameter
Reserved block count:     1228771 . this is the default when the filesystem was created. your filesystem is 32gb and 5% are ~ 2gb. the reservation is for processes running with root account (eg. daemons).
the 5% are are history. today we have filesystems with 1terra or more !!!!. 
use tune2fs to change your reserved-block size, but please don't set it to zero - (200 mb should be enough). i hope this will help. ciao richi

I think I am getting a bit now, should give it a try today. Picture is not still *clear as* an *azure sky of deepest summer.*

---

### Post by SecretCode on 2009-12-31
> **suniyo said:**
> But what if there is say a bug in Transmission bittorrent client? I may lose lot of transfers worth almost 4GB and it is pain to download them again at 512kbps connection. :(

Well ... I don't think fsck is going to delete data. I don't think it's likely that a bug in Transmission is going to corrupt the filesystem. More likely that the partial downloads are somewhere on the drive with restricted permissions.

One question though: is the client currently running? You should terminate it. A possible reason for different tools reporting different free disk space is open files - they can have a different size on disk from what they report to system calls. That's one reason why fsck is run at boot time, or in single user mode, with limited other processes running.

---

### Post by suniyo on 2009-12-31
> **SecretCode said:**
> Well ... I don't think fsck is going to delete data. I don't think it's likely that a bug in Transmission is going to corrupt the filesystem. More likely that the partial downloads are somewhere on the drive with restricted permissions.

One question though: is the client currently running? You should terminate it. A possible reason for different tools reporting different free disk space is open files - they can have a different size on disk from what they report to system calls. That's one reason why fsck is run at boot time, or in single user mode, with limited other processes running.

I think my running TB client is creating some problems. I should restart once before I do anything else. And last message I received about low disk space was about 50MB and after than my TB client has downloaded 257mb of data !! I think should need a restart before anything else.

---

### Post by xifer on 2009-12-31
> **suniyo said:**
> I think my running TB client is creating some problems. I should restart once before I do anything else. And last message I received about low disk space was about 50MB and after than my TB client has downloaded 257mb of data !! I think should need a restart before anything else.

Oh - it's still running?  Don't need to restart yet.  terminate the process(es). then look at the advice above if the disk space is still ''lost''.

---

### Post by suniyo on 2009-12-31
> **xifer said:**
> Oh - it's still running?  Don't need to restart yet.  terminate the process(es). then look at the advice above if the disk space is still ''lost''.

Yes did exactly that. Results are below:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              30G   27G  1.5G  95% /

in terminal.

3.1 GB free in Disk Usage Analyzer.

Any Ideas? Should I run fsck?

---

### Post by xifer on 2009-12-31
Ok, well if you can't find any files in the working directories of the torrent client or other places like /tmp then yes, I think an fsck would not hurt.

---

### Post by suniyo on 2009-12-31
> **xifer said:**
> Ok, well if you can't find any files in the working directories of the torrent client or other places like /tmp then yes, I think an fsck would not hurt.

I just rebooted my computer, now I have to do it again, may be in new year! 
Happy new year to all who helped me. Will report the status after running fsck again. :popcorn:

---

### Post by suniyo on 2009-12-31
> **xifer said:**
> Ok, well if you can't find any files in the working directories of the torrent client or other places like /tmp then yes, I think an fsck would not hurt.

Okey I run fsck in recovery mode and found 2 errors so two blocks recovered and my free space is now 1.6 instead of 1.5 but still it is far away from what Disk UA shows:3.2 GB

I think lost torrent data is somewhere in my home folder as when I scanned the home folder it gave me size equal to 20.1 GB  and when I checked it manually after checking "show hidden files" I got it 21.9GB so the difference is 1.8 GB, almost the difference that the output of this command df -h/ 
```
tusker@tusker-machine:~$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              30G   27G  1.7G  95% /

```

and the Disk usage analyzer shows 3.2GB. 

So one thing is clear now that it is due to lost torrent raw data somewhere in my home folder but where? In my default download location even after ticking "show hidden files" it is not appearing and fsck is not showing any errors as data may be still is "useful" in fsck's eye.

---

### Post by xifer on 2009-12-31
right so login to a terminal session as root to make sure you can see everything.

go to the home directory and have a hunt for any files that should not be there.

```


ls -xalR|more


```

 will show all files

---

### Post by suniyo on 2009-12-31
> **xifer said:**
> right so login to a terminal session as root to make sure you can see everything.

go to the home directory and have a hunt for any files that should not be there.

```


ls -xalR|more


``` will show all files

I have tried it. Results are strange as there are two directories '.' and '..' in my downloads folder. they were drwx------ i changed it to drwxrwxrwx and still they don't appear inside the folder with option "show hidden files" already checked.

Don't know about the size of this two directories. output is pasted below.

```
total 243960
drwxrwxrwx 16 tusker tusker      4096 2010-01-01 01:29 .
drwxrwxrwx  5 tusker tusker      4096 2009-12-09 23:29 ..
drwxr-xr-x  2 tusker tusker      4096 2008-04-11 14:17 AKIRA [1988] [CDRip] [XVID]
drwxr-xr-x  2 tusker tusker      4096 2009-12-21 05:19 Akira Kurosawa - Rashomon (1950) DVDRip Eng Sub (SiRiUs sHaRe)
drwxr-xr-x  2 tusker tusker      4096 2009-12-21 06:13 Derusu.Uzara.DvDRip[1954][RUS]
drwxr-xr-x  2 tusker tusker      4096 2009-12-21 08:06 Dr. Strangelove
drwxr-xr-x  2 tusker tusker      4096 2009-12-31 18:36 Elephant Man
-rw-r--r--  1 tusker tusker 734924800 2010-01-01 03:00 La Chute.avi
drwx------  2 tusker tusker      4096 2009-11-15 20:06 Metropolis.1927.Remastered.464x336.24fps.722kbs.96mp3.MultiSub.WunSeeDee
drwx------  2 tusker tusker      4096 2009-11-15 20:06 Mihai Viteazul
drwxr-xr-x  2 tusker tusker      4096 2009-12-27 23:54 Platoon1986 [DVDRip][h33t][oldsteel]
drwx------  2 tusker tusker      4096 2009-09-16 03:23 Quel maledetto treno blindato
drwxr-xr-x  2 tusker tusker      4096 2009-12-27 23:58 Talvisota
drwxr-xr-x  2 tusker tusker      4096 2009-12-21 06:53 TORA-TORA-TORA@KIDZCORNER H.264 RIP[ENG][HARD SUBBED]
drwx------  2 tusker tusker      4096 2009-09-18 00:33 Trainspotting.1996.DVDRip.x264-VGL
drwx------  2 tusker tusker      4096 2009-10-21 23:38 Up.2009.TS.XVID-FOX-MFDss™
drwx------  3 tusker tusker      4096 2009-10-21 23:53 Vertigo.1958.DVDRip.XviD.MultiSub-CiN
```

Are these directories of my concern both '.' and '..' ? How should I proceed now?

---

### Post by dcstar on 2009-12-31
> **SecretCode said:**
> "But they do" I was thinking ... but in fact only ./VirtualBox is drwxr-xr-x; all the files are -rw-------. Thanks

That is always going to be a problem with a lot of these issues, you either have files that get counted when run in user mode - and miss out on root-only access files, or you run in sudo mode and get the root files and miss out on any files with user-only read rights!

If you don't have your Linux security set up to allow read access for the root group for all your files/folders, then it is almost impossible to use some tools to get accurate results.

---

### Post by SecretCode on 2009-12-31
> **suniyo said:**
> Results are strange as there are two directories '.' and '..' in my downloads folder.

That particular detail isn't strange ... '.' is the directory itself and '..' is the parent directory. You'll find those pseudo-directories in every directory in your system!

---

### Post by SecretCode on 2009-12-31
> **dcstar said:**
> That is always going to be a problem with a lot of these issues, you either have files that get counted when run in user mode - and miss out on root-only access files, or you run in sudo mode and get the root files and miss out on any files with user-only read rights!

**If you don't have your Linux security set up to allow read access** for the root group for all your files/folders, then it is almost impossible to use some tools to get accurate results.

Is there a way to set that up? In the past I just assumed 'root' had read access to everything, regardless of file permissions.

---

### Post by suniyo on 2010-01-01
> **SecretCode said:**
> That particular detail isn't strange ... '.' is the directory itself and '..' is the parent directory. You'll find those pseudo-directories in every directory in your system!

It is very difficult to find those missing files manually as I have millions of files/folders there. 

Is there any mechanism using which I can find 'raw' or 'junk' files in my filesystem or atleast in some particular folder.

---

### Post by SecretCode on 2010-01-01
Without knowing more about the tool, I can't say. Is there a forum for Transmission that you could go and ask at?

---

### Post by joshedmonds on 2010-01-01
I'm pretty sure you got the correct answer for the disk space issue a while ago:

> **rnerwein said:**
> high - i think it's enough - just open a terminal and run followin command as super user (root).
tune2fs -l /dev/your_device and you will see all about your filesystem. look at the parameter
Reserved block count:     1228771 . this is the default when the filesystem was created. your filesystem is 32gb and 5% are ~ 2gb. the reservation is for processes running with root account (eg. daemons).
the 5% are are history. today we have filesystems with 1terra or more !!!!. 
use tune2fs to change your reserved-block size, but please don't set it to zero - (200 mb should be enough). i hope this will help. ciao richi

An ext3/4 file system reserves 5% of the space for the super-user. To see the defaults:

```
man mkfs.ext4
```

```
-m reserved-blocks-percentage
      Specify the percentage of the filesystem blocks reserved for the super-user.  This avoids fragmentation, and  allows  root-owned daemons,  such as syslogd(8), to continue to function correctly after on-privileged processes are prevented from writing to the filesystem.  The default percentage is 5%.
```

This is the best explanation for discrepancies. Also be aware that you may be using tools that measure in different units:

> **geirha said:**
>  Sizes are listed in KiBs btw.

Transmission, for whatever reason (possibly something in the BT protocol?) does not save all of your downloads directly to the disk. To see an example, start a torrent, let it download a while, and look at the Transmission properties for that torrent. Record the amount that you 'Have' and how much has been verified. Now delete the torrent (but not the files) and move the files to another folder. Add the torrent again and point it at the new location. Transmission will verify that a smaller amount has been downloaded.

HTH

---

### Post by xifer on 2010-01-01
> **SecretCode said:**
> Is there a way to set that up? In the past I just assumed 'root' had read access to everything, regardless of file permissions.

root does indeed have access to everything.  which is not always the case when running sudo or when running graphical tools which are normally NOT launched as root.

---

### Post by xifer on 2010-01-01
> **suniyo said:**
> I have tried it. Results are strange as there are two directories '.' and '..' in my downloads folder. they were drwx------ i changed it to drwxrwxrwx and still they don't appear inside the folder with option "show hidden files" already checked.

Don't know about the size of this two directories. output is pasted below.
Are these directories of my concern both '.' and '..' ? How should I proceed now?


As noted - the dots are normal.  But your extract only showed part of the top level.  Is it stupid of me to point out that pressing the space bar when running the command I posted earlier will show the next page?

So if you did page down and read through all the subdirs and there is nothing odd to be seen.  Then the other posters must be correct about the reserved portions.

---

### Post by xifer on 2010-01-01
> **suniyo said:**
> It is very difficult to find those missing files manually as I have millions of files/folders there. 

Is there any mechanism using which I can find 'raw' or 'junk' files in my filesystem or atleast in some particular folder.

sorry - i missed this.  you could  run the ls through a pipe checking and then removing file types.  something like 

ls -xalR|grep .avi

then

ls -xalR|grep -v .avi|grep .dat

and so on checking what's there for a file type, if ok then exclude it and look at what's left

HTH

---

### Post by suniyo on 2010-01-01
> **joshedmonds said:**
> I'm pretty sure you got the correct answer for the disk space issue a while ago:



An ext3/4 file system reserves 5% of the space for the super-user. To see the defaults:

```
man mkfs.ext4
``````
-m reserved-blocks-percentage
      Specify the percentage of the filesystem blocks reserved for the super-user.  This avoids fragmentation, and  allows  root-owned daemons,  such as syslogd(8), to continue to function correctly after on-privileged processes are prevented from writing to the filesystem.  The default percentage is 5%.
```This is the best explanation for discrepancies. Also be aware that you may be using tools that measure in different units:



Transmission, for whatever reason (possibly something in the BT protocol?) does not save all of your downloads directly to the disk. To see an example, start a torrent, let it download a while, and look at the Transmission properties for that torrent. Record the amount that you 'Have' and how much has been verified. Now delete the torrent (but not the files) and move the files to another folder. Add the torrent again and point it at the new location. Transmission will verify that a smaller amount has been downloaded.

HTH


Even if they use different units 1.5gb of difference is too big on 32gb filesystem. I am aware about the torrent explanation you gave as I am an avid user of the protocol and I believe I have not changed my download location since big-bang. 

I think you are right about the reserved space for root, though I need to do some research on that and will be back with my findings. may be this is due to reserved space thing only and data in torrents was actually lost or overwritten.

---

### Post by suniyo on 2010-01-01
> **xifer said:**
> sorry - i missed this.  you could  run the ls through a pipe checking and then removing file types.  something like 

ls -xalR|grep .avi

then

ls -xalR|grep -v .avi|grep .dat

and so on checking what's there for a file type, if ok then exclude it and look at what's left

HTH

Aware about piping and all but I have thousands of folders there in /home/user and kind of non-convenient to post all the output here.

---

### Post by suniyo on 2010-01-01
> **SecretCode said:**
> Without knowing more about the tool, I can't say. Is there a forum for Transmission that you could go and ask at?

Main site: [http://www.transmissionbt.com/](http://www.transmissionbt.com/)
Support and Dev site: [http://trac.transmissionbt.com/](http://trac.transmissionbt.com/)
IRC Channel: irc://irc.freenode.net/#transmission
Forum: [http://forum.transmissionbt.com/](http://forum.transmissionbt.com/)

---

### Post by xifer on 2010-01-02
> **suniyo said:**
> Aware about piping and all but I have thousands of folders there in /home/user and kind of non-convenient to post all the output here.

Actually I wasn't suggesting you post all the output here - rather just read through it yourself gradually filtering out everything that is ok until you are left with any oddities.

---

### Post by suniyo on 2010-01-03
> **xifer said:**
> Actually I wasn't suggesting you post all the output here - rather just read through it yourself gradually filtering out everything that is ok until you are left with any oddities.

It is practically impossible as there are hundred of thousands of files/folders and to view them on terminal window and check it is like doing evil thing to your eyes. May be I need to find and filter out the format in which raw torrent "pieces" are stored on my ubuntu machine. I am really curious about it now. Is it a bug in Transmission bit torrent client or in Ubuntu?

---

