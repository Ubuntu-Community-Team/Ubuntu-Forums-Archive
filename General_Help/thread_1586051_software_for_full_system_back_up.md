---
title: "software for full system back up?"
date: 2010-10-01
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-01
I just moved to Ubuntu. I have been configuring and installing applications so I can finally call this OS my new home. Still not there yet but have been doing alot of work on it.

I was originally with Windows XP. I am a back up freak. I backed up my documents, firefox bookmarks and other important information every 5 mins to another drive when I was using Windows XP. Also, every 24 hours I would have this program Acronis True Image back up the whole Windows partitiong (Drive C). This was so if my hard disk died, I know I could restore the partition from an image and only lose the last 24 hours of configurations/modifications made to the OS.

And for personal data such as bookmarks, messenger chat logs, documents, pictures etc, I would only lose the last 5 minutes of this data, since it was always backed up every 5mins. It was very fast too.

So my question is:

1. Whats the best application to save a whole image of the Ubuntu partition so that it can be restored with minimal (hopefully only 24 hours) of data loss?

2. Whats the best application to save selected directories and have it configured such that those directories are backed up periodically?

3. Whats the best application to do Number 2 (above question) with versioning? That is, if it is backing up periodically, it will save file changes, so we can revert back to an older version of a file.

I have tried SimpleBackUp suggested by the Ubuntu site and did not like it at all. It just said it would run in the background and you couldnt even cancel it or monitor it!

---

### Post by bruno9779 on 2010-10-01
I think the first step should be having /home on a separate partition. All you personal data is stored there.

The rest of the filesystem holds the OS and the program files.

I back up periodically with a cron-job that runs rsync.

Cron is a task scheduler, and rsync is an advanced command line back-up tool.

There are plenty of good tutorials on this forum and on the net, on how get them to work.

cheers

---

### Post by turqoisehex on 2010-10-01
Welcome to Ubuntu ^__^ I use Acronis on XP as well, it's a well made program.

The method I use on Ubuntu is a simple and somewhat old school method, but my backup of choice is tar. 

I like it because I can create different scripts very easily, and have complete control of the backups on every level. For example, here's my full backup script:
```
sudo tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/home/user/.electricsheep --exclude=/home/user/.VirtualBox --exclude=/home/user/.google /
```

That will create a compressed file called backup.tar.bz2 in the directory where I ran the script from. The only manual part is changing the name of the file (adding the date for example).

This way will make daily compressed backups, which means you can go in and pick the day you want the backup from. The real beauty for me of this method is how incredibly easy it is to restore one of the backups, you can do it from a recovery terminal with a single line of code.

To make it more simple, I only run a full backup before installing a new program, updating, changing vital settings, etc. Then I have a script that only backs up my home directory.

If you're paranoid about data loss, you may also want to consider using a raid array of Western Digital Raid Edition drives; I've installed hundreds over the years in small business servers and have yet to see a single one fail.
[http://ncix.com/products/?sku=41075]("http://ncix.com/products/?sku=41075")

If you're looking for something as robust (or potentially far more robust) as Acronis, you should check out Bacula:
[http://www.bacula.org/en/]("http://www.bacula.org/en/")

I've used it in enterprise environments, and while it has a steep learning curve, it's probably the most effective backup program available for Linux. One nice feature is that you can fully manage it via Webmin, which means you can check your backup status from anywhere in the world.

---

### Post by Manyette on 2010-10-01
I agree with turquoisehex, and use tar for my most frequent backups, but for baremetal backup, which I do less often, I use Clonezilla.  I recommend it for that purpose.

---

### Post by psusi on 2010-10-01
You forgot the tar itself in your list of exclusions.  Also you can have the date automatically inserted with `date +%F`.  For example, change the file name to backup-`date +%F`.tar.gz to get backup-2010-10-01.tar.gz.

As for the OP, what are you backing up TO?  If you are using an external hard disk that is large enough, you might want to use rsync.  You can set that up to do an hourly incremental backup where it only has to copy data that has changed, but when you look on the external disk, you will have a folder for each backup that appears to have every file as it was at that time, but only the changed files are actually taking up more space on the disk.  Eventually you can delete some of the older ones if you need space.

---

### Post by pizza-is-good on 2010-10-01
You can use dd to clone your HDD(All your files, links, partitions, file systems; in other words, it is an exact copy, hence it being a cloned drive). If one fails, you just pop in the new one and it works were you left off.
I'm sure you could make a script to have it run on a schedule. There is not compression, so you'd need a drive at least the size of the internal.

---

### Post by psusi on 2010-10-01
You want to use something like clonezilla instead of dd since dd is dumb and copies everything, including free space.

---

### Post by Manyette on 2010-10-01
> **psusi said:**
> You want to use something like clonezilla instead of dd since dd is dumb and copies everything, including free space.

Very true, and it also takes much much longer than clonezilla.

---

### Post by DeMus on 2010-10-01
A completely other solution would be to use a RAID 1 set of drives. You have an instant copy of everything, both system disk and data disk. RAID 1 writes everything to 2 disks simultaneously even though the processor believes there is only 1 disk connected.
Much info can be found on the net.

---

### Post by psusi on 2010-10-01
Raid != backup.

If you overwrite a file on a raid, it's still lost.

---

### Post by DeMus on 2010-10-01
> **psusi said:**
> Raid != backup.

If you overwrite a file on a raid, it's still lost.

How about a "real" back-up? When you changed a file and make a back-up the original version is lost to. So there is no difference.

---

### Post by psusi on 2010-10-01
> **DeMus said:**
> How about a "real" back-up? When you changed a file and make a back-up the original version is lost to. So there is no difference.

That's why you have multiple incremental backups.  Even if you only have one, it still requires two steps to loose your data, not just one required with raid.

---

### Post by Manyette on 2010-10-01
> **psusi said:**
> Raid != backup.

If you overwrite a file on a raid, it's still lost.

And it is SO HARD to get all those drives into my laptop!

---

### Post by fuzzylogic25 on 2010-10-02
THis is how I have structured my partitions. I have two drives:

1. WD Raptor 300GB with partitions:
- NTFS - Windows 7
- NTFS - DATA
- EXT3 - LINUX (root)
- SWAP - LINUX
2. HITACHI 2TB with partition:
- EXT3 - DATA

So basically, my home folder, root folder etc is all in that one linux partition. So I wish to maintain a copy of everything in that EXT3 LINUX partition on the HITACHI drive. so if one drive fails there is always a back up. I do not care for the two NTFS drives.

Now, I was just told by one of the above users that I should have /home on a separate partition but I dont believe all the important data is just held there. For instance, I just installed aMSN and loaded some plugins/skins for them. This was all installed to /usr/share/amsn/plugins & ...../skins. Also, another program that was logging chats also stored it somewhere else other than the /home folder and it didnt allow me to configure the directory.

So thats why I want to back it all up. To be honest, whenever im doing sudo apt-get install....i dont know where these programs are being installed to. Also, I am new to linux and dont even understand what these folders are.

I need to make sure configurations for programs are also backed up because they take alot of time to configure...such as configuring mail, configuring ubuntu desktop apperances, etc etc.


also right now i dont have much time to spend on learning a really complex program for backing up. so command line programs like rsync or boot up programs like clonezilla wont help me. i cant really restart my computer because i have so much stuff running!

---

### Post by Manyette on 2010-10-02
Ummmm - Clonezilla is not a command line program.

---

### Post by fuzzylogic25 on 2010-10-02
yes but its a program that runs at boot? it requires a restart of the OS which i often cant do

---

### Post by Manyette on 2010-10-02
I hate to tell you this, but I don't know of any program that can back up a running system.  I'm willing to be corrected, but to my knowledge, a bare metal backup is not possible of a running system.

---

### Post by fuzzylogic25 on 2010-10-02
thats what i thought too, but acronis true image manages to do it for windows. i dont know if this can be done on linux too. but i hope so!

---

### Post by Manyette on 2010-10-02
Have to tested the Acronis backup done while the system is running under the conditions that it is a bare metal backup.  Frankly, I don't believe it.

---

### Post by fuzzylogic25 on 2010-10-02
thats the thing, i have done it many times and restored such images. and it worked perfect. i know it doesnt make sense, considering files are being modified constantly. but it seems to work fine.

---

### Post by Manyette on 2010-10-02
When I said bare metal, that ASSUMES you have either replaced the hard drive, or have formatted it.  I still have trouble believing that scenario.

---

### Post by psusi on 2010-10-02
Umm... to use Acronis, you boot from a cd, don't you?  Then the system isn't running when you back it up.

---

### Post by fuzzylogic25 on 2010-10-02
oh. really sorry about that. i didnt know what bare metal meant. i was under the impression it meant backing up a whole operating system partition, all files including the MBR.

Thats what acronis does. so when you load windows xp and lets say its in partition C (NTFS), you can back that whole partition up byte for byte even, while its running. But of course to restore the that image, you have to reboot/boot up.

I don't really understand what bare metal means.

but basically I am looking for a utility that will back up the WHOLE partition, not just the /home part but from the / because thats how I made the partition anyway. seems like a lot of logs (like messenger chat logs) and some configuration files for apps go in folders other than /home and i noticed for some of them you cant change the directory. one was logging files to /usr/share/amsn/

---

### Post by Manyette on 2010-10-02
Bare metal means that your hard drive has totally failed, and you have replaced it with a new or different drive.  That's the worst case scenario for a failure, and I know of no backup system which can reproduce and entire system on a new blank drive that has done it while the system is running.  My point was that you have to shut down to have that type of backup, which is necessary if a drive really fails. Thats why I said that I don't do those Clonezilla backups as often.  It's only for the "worst case" scenario.  And a backup of your /home partition using tar is adequate for other scenarios under Ubuntu.  That's why a separate /home partition was recommended.  Ubuntu is that stable.

---

### Post by Manyette on 2010-10-02
That's why I said I did Clonezilla backups less often.  It's only for the worst case failure.  A tar backup of the /home partition is adequate for other scenarios, which is why it was suggested that you have a separate /home partition earlier in this thread.  Ubuntu is that stable.

---

### Post by Quark718 on 2010-10-02
I agree, ubuntu is just that stable.  If ur still just unsure you could always virtualize if you have enough headroom.  I use VMWARE Workstation 7.1..2 and it has automatic snapshots and you can basically set it up to take a snapshot (whole drive image) at whatever interval you want.  The snapshots work like timemachine on the mac.  You can delete a file and go back in time before you deleted it and bring it back.  For that matter you can freeze your session.  Do an update on your machine reboot unfreeze and it's like nothing ever happened.  

Then you can have a script do a tar backup of ur vm folder daily weekly or whatever.  Then you're covered if your entire computer blows up.  I use this feature a lot for my windows based vms but I've never saw the need for ubuntu since it's so rock solid.

That being said there have been updates that have bricked my machine but that's what servers are for.  Sounds like you should just build a server or get a nas type solution like a drobo.  Those things are like raids but it doesn't matter what drives you put it.  You can mix and match.  It's self healing and automatic.

---

### Post by psusi on 2010-10-02
> **Manyette said:**
> That's why I said I did Clonezilla backups less often.  It's only for the worst case failure.  A tar backup of the /home partition is adequate for other scenarios, which is why it was suggested that you have a separate /home partition earlier in this thread.  Ubuntu is that stable.

Tar doesn't know or care if /home is on another partition.

---

### Post by psusi on 2010-10-02
> **Manyette said:**
> That's why I said I did Clonezilla backups less often.  It's only for the worst case failure.  A tar backup of the /home partition is adequate for other scenarios, which is why it was suggested that you have a separate /home partition earlier in this thread.  Ubuntu is that stable.

Tar doesn't know or care if /home is on another partition.

---

### Post by fuzzylogic25 on 2010-10-03
I understand that but its not about ubuntu being stable or not. its about making sure i have a copy of everything in the event that my hard disk dies. Thats the main reason why I back up, because of potential hard disk failure.

/home doesnt contain everything i need. as i said before, i have application config files and other logs in /usr/share/ for example. in the event of a hard disk failure, i would like to have a complete copy of the / partition so i can restore the WHOLE ubuntu OS back to the way it was before the failure. no need to worry about installing anything. do u get me?

---

### Post by Manyette on 2010-10-03
And that is precisely why I suggested Clonezilla.  It creates an exact backup of your entire system.  In your case you may have to do 2 backups ( *I think, since I haven't used Windoze in quite a while* ) one for Windoze and one for Ubuntu, but still, since it is extremely fast, that should not be a problem.  It's only drawback, if you consider it such, is that it has to be restored to a drive which is the same size, or larger.  It cannot be restored to a smaller drive.  And it does restore the entire system, lock stock & barrel!

---

### Post by fuzzylogic25 on 2010-10-03
thanks for that, i really appreciate it. i dont care for the windows partition anymore as i dont use it. i doubt ill ever use it as i usually like to keep a system running and if i have to shut it down, it will be through hibernate.

I wanted to ask, if i do hibernate ubuntu, then run clonezilla next time i boot it up, will it still work? or does it only do it if the system was fully shut down (not hibernated)? this would also mean that it has to save an image of contents in the swap, will it do that?

Also, is there anyway to do a full image of the whole / partition without having to boot up? by that i mean, can you do it while running ubuntu like acronis can with windows?

---

### Post by HermanAB on 2010-10-03
Why???

In 5 years, when your HDD fails, would you want to restore a 5 year old copy of Ubuntu from backup, or would you want to install a new version of Ubuntu?

Backup your data.  Forget about backing up the system. It is a waste of time, since it is faster to install a brand new copy of Ubuntu.

---

### Post by fuzzylogic25 on 2010-10-03
> **HermanAB said:**
> Why???

In 5 years, when your HDD fails, would you want to restore a 5 year old copy of Ubuntu from backup, or would you want to install a new version of Ubuntu?

Backup your data.  Forget about backing up the system. It is a waste of time, since it is faster to install a brand new copy of Ubuntu.


ok well this is what i did with windows. Every 24 or 48 hours, there would be an auto back up of the whole file system. this was good because if my hard disk failed, i could just restore that image and not have to waste time reinstalling software and configuring stuff. This works best for me. It wouldnt be a 5 year old back up. I mean I do this until its time to upgrade to a newer version, but thats not often. I will be sticking to Lucid for a good year at least but would still like to have a back up of the whole system.

---

### Post by Manyette on 2010-10-03
Hi, while I do agree with HermanAB, because I don't really think you realize just how stable linux is, compared to what you're used to, to try and answer your questions, I don't know about the swap. Linux does NOT save the swap partition between boots.  Therefore it is not saved. I believe, but am not certain, that a reboot from hibernate will get you back where you were.  As I said earlier, I do a Clonezilla backup of the system whenever there is a major change to my system, but other than that, I only tar my /home directory, which is where all the real data is located.  The system data is so easily recoverable, just as HermanAB said, that it really isn't worth worrying about. I'm a bit paranoid about backing up my data, but I do think you've got me beat.:)

---

### Post by fuzzylogic25 on 2010-10-03
LOL! yeh i definitely know im very paranoid about backing up. But please understand, it has nothing to do with the stability of linux. I know Linux is very stable and thats the main reason why I moved. However, no matter how stable an operating system is, it can never guarantee a hard disk failure or a power failure (which can create a hard disk failure). Thats what im preparing for, hardware (hard disk) failures.

Now, it may not be a difficult task to install ubuntu again. But I dont want to have to go through installing Ubuntu, all the other software, the gadgets ive configured on my desktop, the fonts and its related sizes for the taskbar, windows etc, panel configs. I know alot of them are stored in the home folder, but it seems like some arnt. and yes maybe it only takes a few hours to set it all up again, but frankly i dont want to do that because im very busy.

I use to install windows, all its applications, configure everything then create an image. If a hard disk failed (and it has before), i just took out another drive, restored an image and I was pretty much ready to go! I just had to copy some of my work files and thats it. I only had to spend 5mins max chosing the image file to restore. saves hours of time!

Thats all i care about, saving time. For all my other important data like documents, ill have some software backing that up to another drive every 10mins or so, its not that big in size. its just text documents, never videos or mp3s. Yep, im a back up freak lol.

---

### Post by psusi on 2010-10-03
On Windows, imaging the whole system is attractive because it takes ages to reinstall windows and then visit dozens of different web sites to download and install software, go through a stack of cds and reinstall those, etc.  The entire process can take days.  This is only a problem for proprietary software though.

It takes only 10 minutes to reinstall Ubuntu, and you can have the package manager save the list of all packages you have installed, then after you reinstall, tell it to reinstall all of them and it takes care of it all while you go have a coffee.

Given that you can get the entire system up and running again in under an hour, without limitations on the size of the new disk, and without carrying forward any cruft and fragmentation from the old one, low level disk imaging looses much of its luster.

---

