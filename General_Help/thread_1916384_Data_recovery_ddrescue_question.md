---
title: "Data recovery ddrescue question"
date: 2012-01-27
forum: General Help
---

### Post by WebNewbie on 2012-01-27
Hi just a quick question.

I've spent literally days researching data recovery. As my storage drive ( second drive in windoze pc ) developed I/O errors, after a power outage.

I've got the general idea of how to use 'ddrescue' to image the faulty drive, to a known good drive.

My question is, what file system am I supposed to use to format the known good drive, or doesn't it matter ?

---

### Post by Venerence on 2012-01-27
It does not matter what is on the target drive when you start a sector by sector file recovery. All partitions get erased and replaced with the partition table from the faulty drive (assuming it is still valid).

Make sure you triple check which drive you are going to. The destination drive will have all data erased on it.

---

### Post by WebNewbie on 2012-01-29
Thanks for the quick response **Venerence**. I managed to aquire a 1.5 TB drive that I formatted to ext3, it was originally formatted to ext4, but apparently, gnu ddrescue doesn't support ext4.

As I am attempting to image a 500 GB NTFS drive, everything I have read so far has no mention of the filesystem used on the recovery drive, strange why none of the guides and how to's don't discribe the preparation of the recovery drive.

I've had too many failed attemps at creating an image of this faulty drive, that I don't want to restart it anymore, incase I damage it any further.

the next time I restart the drive, maybe the last chance I get to recover my photos ! So this time, I need to get this right.

Can anybody advise me if I supply all the info ?

---

### Post by coldraven on 2012-01-29
I have only had experience of using Testdisk to recover my Windows drive so I'm not an expert. AFAIK Venerence is right when he says that the target drive does not need formatting, dd will overwrite everything at a low (system?) level. In short, you get a clone of the faulty drive. Then you can try to recover your data from the clone. There are some good links and advice here:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by dragonfly41 on 2012-01-29
I'm about to start rescuing two windows NTFS partitions in a dual boot configuration.

Although Windows boots up and runs ok (albeit slowly), in ubuntu the windows partitions show "bad sectors" and the two NTFS partitions cannot be seen from ubuntu.

The advice I've read is to switch disks .. soonest.

I've just read here .. [http://ubuntuforums.org/showthread.php?t=1477300](http://ubuntuforums.org/showthread.php?t=1477300)  .. that clonezilla isn't able to clone in presence of errors such as bad sectors.

So I'll try ddrescue. See advice from seeker5528 (post #6).

I've just finished downloading systemrescueCD to try ..

---

### Post by WebNewbie on 2012-01-29
Thanks for the input **Coldraven** another great link to read through. Strange how my searches on Google didn't pickup on that one. It will take me days to get through that lot !

I'm hoping to run TestDisk or PhotoRec on the image that I create, but I can't even get over the first hurdle :(

Data Recovery & Computer Forensics was never meant to be easy, or else, we would all be doing it !

I like to learn new things, and Data Recovery I think is a must these day's. I never had HDD proplems back in the day when ever drive was IDE, now that the 'norm' is to install SATA, I seem to be getting a lot of faulty drives.

---

### Post by WebNewbie on 2012-01-29
Hi **dragonfly41** Yup, me too .... Downloaded Ubuntu System Rescue yesterday. Installed on a USB PenDrive. Maybe this might be of some help to you, you can download all the tools you will need via [http://www.pendrivelinux.com](http://www.pendrivelinux.com) just download the USB Universal Installer.
I even install my distro's with this.

Good luck with your data recovey ....

I usually get stuck with the syntax of ddrescue, INPUT OUTPUT LOGFILE. I would be happy to share any experiences you have learned.
You can also ask any questions from me that you may have, as you seem to have the same problem on your drive that I have. And as I have had many unsuccessfull attempts, I'm pretty sure I know the procedures that don't work.

The 'golden rule' Is, to not attempt a recovery on the damaged drive, it must not be mounted, as you may damage it even more. As far as I know, the data recovery process is attempted using the image file. And some 'in the know' even recomend not to use the original image file, use that as a backup image, a 'master' image as it were. The recovery should be attempted from a duplicate image, makes a great deal of sense to me.

---

### Post by winh8r on 2012-01-29
Hi, a little tip when using DD , remember the correct syntax for the command by training yourself to read it as follows:

dd if (remember this as InputFile, that is the file or device you are taking data from) and the second part of the command is dd of (remember this as OutputFile, that is the file you are moving data to)

You might not have any difficulty remembering, but I thought it was worth posting as I got them mixed up a few years ago and "wrote" an empty partition over the top of the one I was trying to recover!!!!!

Another thing I found useful when running PhotoRec was to only recover one file type at a time from the disk, by selecting a specific file type from the options menu within the utility. This makes it a lot faster and also avoids recovering huge amounts of data that you do not want.

The file selection method also means that the recovery output directory will contain files of only one type and this makes it easier to batch rename your recovered files as you will not have to go through the directory and move all the relevant files before renaming them.

I hope this helps in some small way, good luck with the recovery!!!!

Remember, the key to a successful data recovery session is to set it running , then go away from the computer and do something else! Let the computer have all the resources it needs to do it and it will work faster and more effectively.




edited: open a terminal and type in "  man dd  " for a list of options and brief explanation of functionality.

---

### Post by winh8r on 2012-01-29
> **WebNewbie said:**
> Hi **dragonfly41** Yup, me too .... Downloaded Ubuntu System Rescue yesterday. Installed on a USB PenDrive. Maybe this might be of some help to you, you can download all the tools you will need via [http://www.pendrivelinux.com](http://www.pendrivelinux.com) just download the USB Universal Installer.
I even install my distro's with this.

Good luck with your data recovey ....

I usually get stuck with the syntax of ddrescue, INPUT OUTPUT LOGFILE. I would be happy to share any experiences you have learned.
You can also ask any questions from me that you may have, as you seem to have the same problem on your drive that I have. And as I have had many unsuccessfull attempts, I'm pretty sure I know the procedures that don't work.

The 'golden rule' Is, to not attempt a recovery on the damaged drive, it must not be mounted, as you may damage it even more. As far as I know, the data recovery process is attempted using the image file. And some 'in the know' even recomend not to use the original image file, use that as a backup image, a 'master' image as it were. The recovery should be attempted from a duplicate image, makes a great deal of sense to me.


This is good practice, make a copy of the recovered image and work with that. This means that you will always have a back up of the recovered image should anything go wrong.

As soon as a drive is  suspected of failing it is important to stop using it as soon as possible.

If you are using a drive and accidentally delete some important data then  you need to stop using it as soon as possible if you are to have any hope of successful recovery of that deleted data.

Another point to note, I was told years ago that trying to recover data from the partition you are using is akin to trying to pick yourself up by the ankles!!!!!

As you say, data recovery is a good skill to have nowadays, it might seem like a lot of learning and hard work to some people but I view it in the same way as I view being able to swim, I might not need to do it all the time in my life but it is damn useful in some situations!!!

---

### Post by dragonfly41 on 2012-01-29
I've read good testimonials about Steve Gibson's spinrite for repairing bad sectors.

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

But I'm not sure that $89 is a good investment.   It is cheaper to buy a new drive.  On the other hand  spinrite can be used on all future failing drives.

I read that it can take a very long time to repair a disk (some have said days).

[COLOR=Navy][EDIT] Just after posting the above .. I read this .. software to avoid !

[http://wiki.lunarsoft.net/wiki/Data_Recovery](http://wiki.lunarsoft.net/wiki/Data_Recovery)
[/COLOR]

---

### Post by Venerence on 2012-01-29
A couple things I'll say when using ddrescue (I've recovered 20-something failed hard-drives using it).

You can recover directly to a new hard-drive. It does support making an image, but as far as I use it I always just go directly from drive to drive.

It is the best program you can use to recover your data. However, keep in mind it can take a *long* time to recover the data. The main drawback is that it waits 30 seconds to time out on every bad sector. This means, that if you have 1k+ bad sectors on your drive (which is not all that uncommon), it can take upwards of a **week** to get everything. (I have made a previous post seeing if the timeout can be lowered, but so far nobody has said anything).

Bottom line is to be patient. It will take a long time, but it will get everything that is possible to get. Once it is finished, you can perform a file system check on the drive (ubuntu has it built into the disk manager), and then everything that you're going to get will be available (barring massive data recovery specialist charges).

Typically speaking, the command I use is the following (assuming sda is the source and sdb is the destination):

sudo ddrescue -f -n /dev/sda /dev/sdb rescue.log

again, and I can't stress this enough, make *sure* the source and destination are correct. You can check the appropriate drive letters in the ubuntu disk manager.

PS: if someone can tell me how to lower the I/O timeout for a hard-drive within ubuntu, I will give you lots and lots of money. Honestly, this is the only barrier to making this the perfect software level data recovery program.

---

### Post by winh8r on 2012-01-29
I use the Ultimate Boot CD to repair minor issues on HDD's. I have found that the utility called MHDD is the most effective. 

Be aware that it is well worth taking the time to read up on these utilities before attempting to use them as they are low level editing tools and can completely alter the geometry and operating parameters of the hdd, to the point of leaving you with a 250Gb paperweight if you get it wrong!


You can get the Ultimate Boot CD for free from here:

[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")

---

### Post by Venerence on 2012-01-29
also: do not use spinrite, hdd regenerator or mhdd to "fix" bad sectors. Those programs work by guessing what was in the bad sectors and remapping them to a good part of the drive. Bad sectors on a failing hard-drive have an avalanche effect. You may fix your hard-drive for a week to a month. You may also find that when it fails again (and it will fail again), you lose everything.

If you can still boot to your OS on your drive, typically speaking it is possible to recover all your information. However, the drive it is originally on is no longer useable or trustworthy. Get your information off it, and never use it again. Do not use it except to get your information off it. Every time you use your drive, the more likely it is you will lose everything on it.

---

### Post by dragonfly41 on 2012-01-29
> The main drawback is that it waits 30 seconds to time out on every bad  sector. This means, that if you have 1k+ bad sectors on your drive  (which is not all that uncommon), it can take upwards of a **week** to get everything. (I have made a previous post seeing if the timeout can be lowered, but so far nobody has said anything).Would it not be easier to just backup files from disk A to disk B (a freshly prepared drive) using say gnome commander from a Live CD?

Search for gnome-commander (a two panel file manager similar to Windows Total Commander)  in Synaptic Package Manager.

Setup your two panels as input and output.

Then copy (F5) one folder at a time in the background.   This allows more incremental backup which can be scripted.

---

### Post by Venerence on 2012-01-29
> **dragonfly41 said:**
> Would it not be easier to just backup files from disk A to disk B (a freshly prepared drive) using say gnome commander from a Live CD?

Search for gnome-commander (a two panel file manager similar to Windows Total Commander)  in Synaptic Package Manager.

Setup your two panels as input and output.

Then copy (F5) one folder at a time in the background.   This allows more incremental backup which can be scripted.

90% of backup programs cannot cope with failing hard-drives. As soon as it hits a bad sector, the program will crash, or wait for your input (which if it does on 5,000 files, it may as well be worthless).

Furthermore, you lose far more information trying to copy data from a corrupt filing system then if you repair the filing system before copying. You cannot repair the filing system on a failing hard-drive because it may try to repair it to more bad sectors, or even cause the hard-drive to fail even farther.

The only safe way to copy information off a failing hard-drive is to do a low level data recovery to a second drive, repair the filing system and then copy the information. This is what ddrescue is designed to do.

---

### Post by dragonfly41 on 2012-01-29
We are discussing two issues here ..

(a) being able to backup incrementally rather than leaving the computer running for up to a week

(b) recovering from impact of bad sectors.

All the advice I've read is to get your data off your suspect disk .. as soon as possible .. and only then try to recover the transferred content from the "good" disk.

With a file manager at least some large tracts of files might be recovered before the disk gives up the ghost at any time (although it might hang on for years).

I've decided to avoid spinrite etc. and just transfer important content .. chunk by chunk to a "good" disk .. and then throw the failing disk showing bad sectors.

I've got about 90 bad sectors in one NTFS partition and 20 bad sectors in another.

---

### Post by Venerence on 2012-01-29
> **dragonfly41 said:**
> We are discussing two issues here ..

(a) being able to backup incrementally rather than leaving the computer running for up to a week

(b) recovering from impact of bad sectors.

All the advice I've read is to get your data off your suspect disk .. as soon as possible .. and only then try to recover the transferred content from the "good" disk.

With a file manager at least some large tracts of files might be recovered before the disk gives up the ghost at any time (although it might hang on for years).

I've decided to avoid spinrite etc. and just transfer important content .. chunk by chunk to a "good" disk .. and then throw the failing disk showing bad sectors.

I've got about 90 bad sectors in one NTFS partition and 20 bad sectors in another.

The issue is not with the amount of data being recovered, it is with how the data is accessed.

It honestly depends on how far the drive has failed. The problem with doing a file-by-file recovery (besides the fact that the copy is being done from an unclean filesystem), is that the physical sectors are being accessed randomly.

Depending on how the drive has failed, randomly accessing the sectors on a bad drive can cause the drive to instantly catastrophically fail.

The idea behind a sector by sector recovery is that all data on the drive is accessed sequentially. This means that the physical heads on the drive do as little movement as possible, which vastly increases the chances of recovering everything.

Furthermore, once everything has been moved onto a clean drive, the filing system can be properly repaired. This gives you the best chance of getting everything.

All this of course depends on how far the drive has failed. If there are only 1-50 bad sectors, then yes a regular old file copy can get everything you need. If there are 500+ bad sectors, you may only recover a tenth of the information you need. Worse, you may kill the drive. The only safe way is sector by sector.

---

### Post by WebNewbie on 2012-01-29
Thanks chaps for the very informative replies. Very much appreciated. One of the reasons why this is taking me days, weeks in fact. Is the fact that I have researched it before taking the plundge. For what I consider to be my very important data. Over 5000 digital photos, most of them irreplaceable.

I run two system, 1 windoze XP *( which is the one that damaged my hard drive )*, 2nd PC running Linux Ubuntu 10.04 LTS *( which is now my 'recovery PC' )*.

I discovered early on that 'SpinRight', is a definate NO NO, as it writes back to the damaged drive. And DD halts on errors, So I came to the conclusion that GNU DD_rescue is the one to use. After all, Computer Forensics Experts use it ! If it's good enougth for them, it's good enougth for me;)

**venerence** A couple of questions on the syntax you suggest;

[sudo ddrescue -f -n /dev/sda /dev/sdb rescue.log]

Do I have to use the **-f** & **-n** flags ?

As I didn't want make the classic mistake that a lot of people are making, ie, getting the 'Source drive' & 'Target drive' mixed up, I simply put some post-its on the apropriate drives, like so;

/dev/sdd *( which is my source drive = damaged drive )*
/dev/sdb *( which is my target drive = healthy drive )*

The final question I have before I try again is, on your suggestion, you have the location of the logfile going onto the image drive, I want to put my logfile on my desktop ( bearing in mind that I am running off a USB pendrive ) would my syntax here be correct ?

# sudo ddrescue -r3 /dev/sdd /dev/sdb/xray.img /Desktop/xray.log

I'm going for x3 retries. I know there's a lot of data to recover, and it might take weeks, but the PC is going nowhere, and I still have windoze PC to continue the research.

---

### Post by Venerence on 2012-01-29
Don't bother with the -retry flag. It's technically there for advanced recovery, but in all my experience in data recovery (5+ years of doing such), once a bad sector happens, there is no possible way to get the information out of it. Doing the retries is just beating a dead horse.

the -f flag is there just to avoid the program complaining. If there is any partitions present on the destination drive, or if a log file already exists, the program will complain without -f being enabled. As long as you triple check the source and destination, you should include the -f.

the -n flag is there so it doesn't try to rehash bad sectors (similar to the -retry flag). It will still trim however, so it is worth including.

BTW, if you want to know what the program does when it trims, let me know. Bottom line though, even with the -n flag, it will still trim the bad sectors after completion. The -n flag just prevents it thrashing itself over stuff it won't copy regardless.

As far as the log file destination is concerned, I *always* do the recovery via booting the install disk. You don't have to of course (as long as your ubuntu boot is on a non failing disk), but the rescue.log file will be created in whatever location your terminal is in. So if you are in /home/documents, for example, the log file will be created in that location. The source and destination in ddrescue are not related to where the log file is created.

PS: don't trust the assignments given based on a previous boot. They may reassign based on what it detects. Check in disk manager for ubuntu before doing any recovery.

---

### Post by dragonfly41 on 2012-01-29
> 
Over 5000 digital photos, most of them irreplaceable.

...

And DD halts on errors, So I came to the conclusion that GNU DD_rescue is the one to use. After all, Computer Forensics Experts use it !



Did you see the earlier link I posted which does not recommend **dd_rescue**

[http://wiki.lunarsoft.net/wiki/Data_Recovery](http://wiki.lunarsoft.net/wiki/Data_Recovery)

...

I've had various disks fail on me in the past (invariably due to windows).

One of the problems I found .. e.g. in using testdisk and photorec .. was that filenames were not recovered.  A problem if you have 5000 named images.

I must say I got good results in running windows file recovery utilities.

The corrupt disk is removed and accessed as an external drive to attempt a recovery.

The products which worked well for me (including recovery of file with names) were

Recover My Files
[http://www.getdata.com/](http://www.getdata.com/) 

Stellar Phoenix
[http://www.stellarinfo.com/](http://www.stellarinfo.com/)

.. but both come at a price although you can "try before buy".

---

### Post by WebNewbie on 2012-01-29
Mmmmmmmmm ... that's interesting **venerence** . OK, i'll drop the -r flag. All I really want to acheive right now is, a direct replica of the faulty drive.

So my syntax should look like this;

# sudo ddrescue -n -f /dev/sdd /dev/sdb/xray.img /Desktop/xray.log

Just to clarify what I have so you get the picture, my recovery setup is as follows;

Linux machine with internal 500GB SATA HDD /dev/sda ( system )
internal SATA HDD 1.5 TB /dev/sdb ( recovery drive )

Damaged drive removed from windozw pc, connect via USB adapter.
Only turned on when I'm ready to'DD' !

I will of course check with where my USB will be mounted.
I usually use **fdisk -l**, is there a better way ?

---

### Post by Venerence on 2012-01-29
> **dragonfly41 said:**
> Did you see the earlier link I posted which does not recommend **dd_rescue**

[http://wiki.lunarsoft.net/wiki/Data_Recovery](http://wiki.lunarsoft.net/wiki/Data_Recovery)

...

I've had various disks fail on me in the past (invariably due to windows).

One of the problems I found .. e.g. in using testdisk and photorec .. was that filenames were not recovered.  A problem if you have 5000 named images.

I must say I got good results in running windows file recovery utilities.

The corrupt disk is removed and accessed as an external drive to attempt a recovery.

The products which worked well for me (including recovery of file with names) were

Recover My Files
[http://www.getdata.com/](http://www.getdata.com/) 

Stellar Phoenix
[http://www.stellarinfo.com/](http://www.stellarinfo.com/)

.. but both come at a price although you can "try before buy".

Every problem you have mentioned has absolutely nothing to do with a physically failing hard-drive. All of those issues have to do with accidentally deleting files, partitions, or both.

None of those programs or solutions would help the OP in any way whatsoever.

PS: there is absolutely no situation where a file will be deleted that you needed "due to windows". It is something you did or a program you downloaded that caused it. I am fully sick of people blaming things they did on "windows".

---

### Post by Venerence on 2012-01-29
> **WebNewbie said:**
> Mmmmmmmmm ... that's interesting **venerence** . OK, i'll drop the -r flag. All I really want to acheive right now is, a direct replica of the faulty drive.

So my syntax should look like this;

# sudo ddrescue -n -f /dev/sdd /dev/sdb/xray.img /Desktop/xray.log

Just to clarify what I have so you get the picture, my recovery setup is as follows;

Linux machine with internal 500GB SATA HDD /dev/sda ( system )
internal SATA HDD 1.5 TB /dev/sdb ( recovery drive )

Damaged drive removed from windozw pc, connect via USB adapter.
Only turned on when I'm ready to'DD' !

I will of course check with where my USB will be mounted.
I usually use **fdisk -l**, is there a better way ?

To be honest I have no experience of using ddrescue to recover to an image file, but theoretically that should be fine. Mounting that image file to recover the images is something I wouldn't be able to help you with (we had plenty of spare drives to recover onto, so we didn't worry about it).

Keep in mind that it is always better to plug a drive directly via sata/ide cable to a computer then with a usb adapter. There is some information the hard-drive firmware simply can't send via a usb. Furthermore, a usb adapter may not properly handle all the statuses the HDD is trying to send to the bios.

As far as fdisk is concerned, that's perfectly fine. Ubuntu disk manager simply provides a gui interface for that info.

---

### Post by WebNewbie on 2012-01-29
OK, let me explain.
I never accused windows of loosing my data, all that happen was, I had a powercut at home. when I rebooted my windows pc, the drive wasn't showing.

First I tried to run 'RecoverMyFiles v4.6', but the drive wasn't showing at all. That's when I took it out and plugged it into my Ubuntu machine via a USB adaptor, that's the stage I'm at currently.

So this must mean that the file system is currupt right ?

**dd_rescue** I understood as being the correct term for the GNU version, as oposed to the other confusingly name ddrescue, which is a different version.

---

### Post by Venerence on 2012-01-29
> **WebNewbie said:**
> OK, let me explain.
I never accused windows of loosing my data, all that happen was, I had a powercut at home. when I rebooted my windows pc, the drive wasn't showing.

First I tried to run 'RecoverMyFiles v4.6', but the drive wasn't showing at all. That's when I took it out and plugged it into my Ubuntu machine via a USB adaptor, that's the stage I'm at currently.

So this must mean that the file system is currupt right ?

**dd_rescue** I understood as being the correct term for the GNU version, as oposed to the other confusingly name ddrescue, which is a different version.

Everything you have brought up is perfectly valid, it was more the other person posting that I had issues with.

There are two different versions of ddrescue, one that just used linux commands to recover data. The later version (in ubuntu referred to as gddrescue) kept a log file that it could refer to. This allowed features as continuing after an interruption, reversing the direction of data recovery, or parsing the log file to find out what files were actually corrupted (something I haven't gone into yet).

You can download the .deb file for the correct ddrescue from the following: [http://packages.debian.org/sid/i386/gddrescue/download]("http://packages.debian.org/sid/i386/gddrescue/download"). You can install this by copying it to the terminal location then typing: sudo dpkg -i <filename>.

---

### Post by WebNewbie on 2012-01-29
Personally, I would prefere to connect the faulty drive internally and use the recovery drive on the USB adapter.
Or, better still, have all drives connected to internal usb ports, but this motherboard only has 2.

The reason I did it this was, I read in another post that the OS will mount the damaged drive on boot. This way, at least I can turn it on when rquired.

You think I should try to repair the file system ?
when I turned on the USB adaptor yesterday, I could see my folders, when I opened the folder it was empty !

what am I doing wrong ?

---

### Post by Venerence on 2012-01-29
> **WebNewbie said:**
> Personally, I would prefere to connect the faulty drive internally and use the recovery drive on the USB adapter.
Or, better still, have all drives connected to internal usb ports, but this motherboard only has 2.

The reason I did it this was, I read in another post that the OS will mount the damaged drive on boot. This way, at least I can turn it on when rquired.

You think I should try to repair the file system ?
when I turned on the USB adaptor yesterday, I could see my folders, when I opened the folder it was empty !

what am I doing wrong ?
You shouldn't trust anything on the source drive until you do a low level data recovery from the drive.

The best idea is to plug both drives in (internally preferably). Boot off the ubuntu install disk, and install gddrescue via the download link I gave you.

After performing the data recovery, open up the destination drive via the ubuntu disk manager and repair the filing system (if it is linux). Otherwise, boot into windows afterwards and perform a chkdsk. Once you have done that, all files that you can see is the files you have recovered. Anything that is missing is unrecoverable (without spending 10,000 dollars or more). That is your best path to getting your info.

PS: don't try repairing the filing system on the source drive. You could end up killing the drive. Only repair the filing system or do a chkdsk after your have done a sector-by-sector to the new drive.

---

### Post by dragonfly41 on 2012-01-29
> [COLOR=Blue]Every problem you have mentioned has absolutely nothing to do with a  physically failing hard-drive. All of those issues have to do with  accidentally deleting files, partitions, or both.

None of those programs or solutions would help the OP in any way whatsoever.[/COLOR] [COLOR=Blue]

PS: there is absolutely no situation where a file will be deleted that  you needed "due to windows". It is something you did or a program you  downloaded that caused it. I am fully sick of people blaming things they  did on "windows".[/COLOR] 


I beg to differ. Files have been corrupted and came close to being lost when there have been forced power downs on windows.    Of course these glitches *can *be due to "something I did" .. such as forced power down when windows freezes .. but rarely due to rogue programs downloaded or viruses.  

I am not "blaming" windows. I have used windows for many years and will continue to do so because I have to. 

One becomes used to recovering from crashes on windows from time to time.

On the matter of data recovery (the subject of the post) if the OP wishes to have 5000 recovered photos named file0001.jpg to file4999.jpg (if lucky) then go ahead trying out free utilities.

---

### Post by Gazucha on 2012-01-29
Hi all,
 my first post so excuse me if it is in the wrong area. 
In mid December after months of receiving annoying Ubuntu 11.10 (from 11.04) Upgrade pop-ups, I regretfully pushed the the 'Upgrade Now' button and that was the end of my computer as I knew it. No 11.10 and no 11.04 and absolutely NO access to almost a years work and tutorial downloads (about 110gigs)
 Being ignorant I then thought I would merely reinstall 11.04. That just made things worse. I tried sooo many commands over almost 2 weeks that I lost count. Some days I spent a full 12 hours before I gave up. 
What I eventually did was boot from the 11.04 CD and download an 11.10 CD which is where we are now. But STILL no access to my 110Gb file system!!!!:( It's there and when I try to open the folder it has two files, one 'access your private data' and one 'read me.txt' when I open the private data I get ... This link cannot be used, because its target "/usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop" doesn't exist.


 Would this DDRescue thing work for me?

 Any help and I will love you forever..

---

### Post by Venerence on 2012-01-29
> **dragonfly41 said:**
> I beg to differ. Files have been corrupted and came close to being lost when there have been forced power downs on windows.    Of course these glitches *can *be due to "something I did" .. such as forced power down when windows freezes .. but rarely due to rogue programs downloaded or viruses.  

I am not "blaming" windows. I have used windows for many years and will continue to do so because I have to. 

One becomes used to recovering from crashes on windows from time to time.

On the matter of data recovery (the subject of the post) if the OP wishes to have 5000 recovered photos named file0001.jpg to file4999.jpg (if lucky) then go ahead trying out free utilities.

The only time you would lose the file names is if the MFT (master file table) became corrupt or lost. This can only happen if the first 10,000 sectors became corrupted (unlikely) or the partition table is deleted.

The chances of this happening on a recoverable failed hard-drive is almost none. At least, if this information got corrupted, then the rest of the drive is unrecoverable as well.

Bottom line, if you lose this information, it is either something that you did, or the drive is so damaged you wouldn't have gotten the files anyway.

---

### Post by Venerence on 2012-01-29
> **Gazucha said:**
> Hi all,
 my first post so excuse me if it is in the wrong area. 
In mid December after months of receiving annoying Ubuntu 11.10 (from 11.04) Upgrade pop-ups, I regretfully pushed the the 'Upgrade Now' button and that was the end of my computer as I knew it. No 11.10 and no 11.04 and absolutely NO access to almost a years work and tutorial downloads (about 110gigs)
 Being ignorant I then thought I would merely reinstall 11.04. That just made things worse. I tried sooo many commands over almost 2 weeks that I lost count. Some days I spent a full 12 hours before I gave up. 
What I eventually did was boot from the 11.04 CD and download an 11.10 CD which is where we are now. But STILL no access to my 110Gb file system!!!!:( It's there and when I try to open the folder it has two files, one 'access your private data' and one 'read me.txt' when I open the private data I get ... This link cannot be used, because its target "/usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop" doesn't exist.


 Would this DDRescue thing work for me?

 Any help and I will love you forever..

DDrescue would not help you. Furthermore, since ext3/4 partitions defrag within real time, any information you had accidentally deleted is most likely lost. Unfortunately, there is no chance to recover that info.

For future reference, if you want to recover any file you accidentally delete, you must immediately turn off your system and never use it again until you get it recovered. For linux especially, any information you delete is nearly immediately erased afterwards. For windows, you have a slim window of time before the unallocated space gets overwritten.

---

### Post by WebNewbie on 2012-01-29
Thanks for the help **Venerence** greatly appreciated. I think a lot of people would be tearing their hair out by now, But I seem to be having great fun :D * ( what else are Sunday afternoons for ? )*

Reading other posts, threads and various forums, it seems to me that most people are always in a rush to perform any recovery of any type, as no two are the same, the research is essential.

Anyway, I just need to double check the ddrescue options.

ddrescue -n -f /dev/sdd /dev/sdb/xray.img /Desktop/xray.log

The above is the command I use, however, I got an invalid option error. Should the **-f** flag, of been an upper case **-F** flag ?

As I always seem to make a positive from a negative, the error didn't get the ball rolling, as it were.
So now I will disconnect everything, and connect all drive internally, and boot from the SystemRescue USB. My other option is to use RIPLinux, as that is also on the USB pendrive.

Both have gddrescue on them I beleive. I hope a lot of people are following this thread, as they will also learn a great deal from you. I know I have.

---

### Post by Venerence on 2012-01-29
> **WebNewbie said:**
> Thanks for the help **Venerence** greatly appreciated. I think a lot of people would be tearing their hair out by now, But I seem to be having great fun :D * ( what else are Sunday afternoons for ? )*

Reading other posts, threads and various forums, it seems to me that most people are always in a rush to perform any recovery of any type, as no two are the same, the research is essential.

Anyway, I just need to double check the ddrescue options.

ddrescue -n -f /dev/sdd /dev/sdb/xray.img /Desktop/xray.log

The above is the command I use, however, I got an invalid option error. Should the **-f** flag, of been an upper case **-F** flag ?

As I always seem to make a positive from a negative, the error didn't get the ball rolling, as it were.
So now I will disconnect everything, and connect all drive internally, and boot from the SystemRescue USB. My other option is to use RIPLinux, as that is also on the USB pendrive.

Both have gddrescue on them I beleive. I hope a lot of people are following this thread, as they will also learn a great deal from you. I know I have.

Make sure you add sudo before all of it to give the command administrator privelages. You definitely want to use the lower case -f (-F invokes the fill command, which you don't want). Try making the log file in the same directory you're using the command (for example, I cd to the /Documents folder first and then create the log file in there).

Also, as I said before, I have no experience recovering to an image file. If you were recovering to a secondary drive directly I may be of more help.

What I would try is doing cd Documents

then sudo ddrescue -f -n /dev/sdd /dev/sdb/image.img recovery.log

I would say the error is due to the forward slash at the beginning of the log file. If you remove that, it would probably work.


Also last post before sleep (Australia time)

---

### Post by WebNewbie on 2012-01-29
Thanks **Venerence** pleasant dreams :)

I'll let you know how I got on, as I try to learn a new thing everyday, I hope that this thread will end on the note [SOLVED].

---

### Post by Gazucha on 2012-01-29
Unfortunately, there is no chance to recover that info.

So, countless hours of specialist work,1000's of photo's, contacts, passwords etc etc. (my recent life) all lost because Ubuntu are sending out dodgy software. 
 I actually did not want to upgrade but I kept getting hassled.
 So what is on the 110gig file system if not my old files?:confused:

---

### Post by dragonfly41 on 2012-01-29
Gazucha

You'll get lots of advice here on the need for backup .. or that it was "user error" .. but it doesn't help you.

Here is a similar scenario ..

[http://ubuntuforums.org/showthread.php?t=1846898](http://ubuntuforums.org/showthread.php?t=1846898)


In your shoes I would follow the steps I've used with some success before ..

(a) stop using your disk.

(b) carefully remove it physically from your PC and fit it into a USB enclosure you can buy from say Maplin or other store (if you haven't done this before get help from someone who has).

(c) plug your problem disk now in USB enclosure into another working PC as an external device.

(d) download one of the more professional (not free) recovery programs which run on windows.   I gave two examples in an earlier post  (see my post #20 with links).

(e) before committing to buying .. use the analysis mode see if one of these recovery programs can detect any of your lost files in the external drive (it is likely that your files they will have been overwritten by your ubuntu upgrade but even so there is a slim possibility of recovery of some).

(f) if any files can be detected you will need to buy the licence for the recovery program and  leave running perhaps overnight.

(g) have enough free space available to copy any recovered files.

...

You can also use linux recovery disks to try to recover as advised elsewhere (including in this thread).

But if recovering in a windows host environment your target disk will need to be in an external enclosure.

Good luck.

---

### Post by WebNewbie on 2012-01-31
Hi all,

Just a friendly tip ~
First take a _real close look_ at your faulty drive. I spent days researching data recovery programs, and how to use them. Hence the very first question on this post. I agree lots of valuable information here, only, nothing pertains to the problem I may have. One of the responses from a member on here, got me looking closer at my faulty drive.

The 1st image below shows the controller board on a good 500GB Seagate drive, the 2nd image is my faulty drive, also a Seagate 500GB.

If I'm not mistaken, those are dry solder joints !
It so happens both drives have the same firmware versions, I have't quite worked out the date codes as yet, I don't think that will matter too much. My idea is to change the controller boards.

Anybody done this before ?

---

### Post by mips on 2012-01-31
> **dragonfly41 said:**
> I've read good testimonials about Steve Gibson's spinrite for repairing bad sectors.

Stay away! Might have been good 20yrs ago but these days it's of very little use and could cause potentially more damage than do any good. It will just make a dying drive worse.

---

### Post by mips on 2012-01-31
> **WebNewbie said:**
> 
If I'm not mistaken, those are dry solder joints !

It so happens both drives have the same firmware versions, I have't quite worked out the date codes as yet, I don't think that will matter too much. My idea is to change the controller boards.

Anybody done this before ?

I don't see what you see. Secondly there is no solder on the bottom of the board, just the exposed copper vias/pads. Think you are on a wild goose chase here.

Swapping logic boards is not always that simple. Drives are manufactured with defects, the defects and particulars of the drive are stored in the G-List & P-List. This information is unique for every drive out there. The platter defects are related to the eeprom programming on the logic board (or reprogram it). In most cases where you swap the logic board you also have to desolder the eeprom from the original board and solder it onto the replacement board. There are some exceptions to this though.

Contrary to advice here I would suggest you don't recover data from a drive via USB. The USB-SATA/PATA conversion can cause problems.

When using dd rescue I have stopped the recovery before at the point where the errors start and then restart it with a big jump ahead to try and get past the problematic area and continue recovering so I can get as much stuff off as fast as possible. I then go back and let it recover from the spot where I initially stopped it. I don;t always leave things up to the built in algorithms.

---

### Post by WebNewbie on 2012-02-01
Thanks **mips**, good advice. I understand what you're saying about the solder joints, ya, I know they're on the oposite side of the controller board, and what I am actually seeing is the underside of the board. What I was trying to point out, in a shortened form, heat damage. Those connections just don't look right to me.

I'm not trying to advise others to do this, this will be my 'last chance saloon', hopefully I will not need to do this, others have tried, and gotten away with it ! if it worked for them, may it'll work for me ;)

My original post was a question on how to image the faulty drive.
I haven't even got to the stage of recovering the data. when the faulty drive was connected, on a few occasions via USB, sometimes it would show, sometimes not. So I built a 'dedicated recovery system', first drive= recover drive, second drive= faulty drive, and booted off USB pendrive linux where i have my recover tools and imaging tools. Doing this way, was worst ..... the only drive detected was the first drive.

I have I/O errors, the drive is spinning, sounds OK too.
What's my next step ?

Changing controller boards, last resort. still won't let go of my 5000 + photos yet though. I'm treating this as a valuable learning experience.

---

### Post by mips on 2012-02-01
Could you paste ALL of the details regarding the drive on the top sticker/label (make, model, s/n, manufacture code, FW etc etc etc). A clear photo will be even better.

---

### Post by WebNewbie on 2012-02-01
Hi **mips**. Sure, not a problem.
I'll be back in a mo ;)

---

### Post by WebNewbie on 2012-02-01
Hi **mips** Sorry it took a while longer than I thought ..... had to setup a macro photography area :D

Here's the info if it helps

The 1st image is the good disk
The 2nd image firmware & manufacture date
The 3rd image is the bad disk
The 4th image firmware & manufacture date

I haven't removed the controller board yet, I dread to think what I will find on the other side.

For those of you who may be interested. Seagate don't print the manufacture dates on the drives like Western Digital. Seagate use a 5 digit code, if you need to find out when your drive was manufactured.
Here is the link for their date calculator : [http://www.bugaco.com/calculators/seagate_date_code.php](http://www.bugaco.com/calculators/seagate_date_code.php)

In my case, the drives were manufactured in the same factory, 3 months apart ! February & April 2010.

---

### Post by mips on 2012-02-01
Will get back to you in the morning.

Can you post the smart data for the faulty drive and any specific details of the I/O errors you are getting, error messages etc. Are the I/O errors constant or only at certain times. You mentioned bad sectors in a earlier post, how prevalent are they and do you now the location/range they span? Sounds like you have head or platter issues.

Do you have another drive that's bigger than 500GB or has more than 500GB of free space.

---

### Post by Claus7 on 2012-02-01
Hello,

[just a parenthesis]

I have not read all the thread, just that you faced input output errors. I had faced exactly the same problem trying with ddrescue, testdisk and other things I do not remember at the time, to rescue some things. If you would like them to be rescued with the correct names, I think that it will be extremely difficult (your files that is). I was able in the end to rescue some files (binary ones, trajectory files), yet we were not able to identify them. Apart from that, some pdf files was impossible to open, since they were split in different areas.

No matter what are you trying to do: don't plug in and out a lot of times your disk. Make sure that you know what you are doing and then just do it. Do not try to write new things on the faulty disk. 

I hope that you are going to face a much better situation than me at the time.

[end of parenthesis]

Good luck,
Regards!

---

### Post by mips on 2012-02-02
Also run MHDD on the drive for up to the point where the errors start then save a screenshot of it, MHDD saves the screenshot in text format. Post it here.

Edit: Oh, and enable the logging on MHDD.

MHDD is a dos based app, to make a bootable usb stick just google "128mddos.img", download it and write the image to a flash stick, copy mhdd onto it.

---

### Post by WebNewbie on 2012-02-02
Thanks for your patience **mips** as always, excellent advice.
I started another thread on here, concerning hardware detection. As the drive isn't being seen when connected internally. A few day's ago I connected the drive via a USB SATA adaptor, and booted from my trusty Pendrive. I checked with disk utility, and SMART was off / disabled.

I'll try the MHDD app, you suggest, sounds rather complicated. But I think I'll manage. I have a spare 1.5 TB WD drive, at the ready, sole purpose is for the disk image. I'm not trying to recover direclty off the faulty drive. The whole point of this exercise, is to image the faulty drive, then do the recovery from the image on the good drive.

---

### Post by dragonfly41 on 2012-02-02
Nobody has yet mentioned an old trick - written up in different blogs - of putting the "bad" disk in deep freeze (suitably sealed in plastic bag to protect against water ingress) and then trying to rescue the data .. quickly .. to a backup drive before the frozen disk thaws out.   

Some even suggest putting the disk in a USB enclosure (but clearly not mains powered!!) and with a suitably long connector cable keeping the disk in deep freeze while the data recovery is completed on a laptop near the freezer.

*I haven't tried this trick myself and I don't know if it is a myth.*

But some report bringing dead disks back to life for a short period (30-60 minutes window) to allow data recovery (have your ddrescue scripts and backup drive ready to spring immediately into action). 

If you are resorting to inspecting dry solder joints then this deep freeze theory seems to be on a par with that option.

More here ...

[http://www.google.com/search?q=recover+disk+in+freezer](http://www.google.com/search?q=recover+disk+in+freezer)

The risk is that taking the frozen disk back into a warm room environment will cause internal condensation and rapidly accelerate disk failure.

As posted here ..

[http://superuser.com/questions/1078/harddrive-in-the-freezer-ever-work-for-you](http://superuser.com/questions/1078/harddrive-in-the-freezer-ever-work-for-you)

it is a "last chance" approach.

**[COLOR=Red]Do this at your own risk if all else fails  !!![/COLOR]**

What do the disk experts here think of this technique?   Any success reports?

---

### Post by WebNewbie on 2012-02-02
I've read various articles about the deep freeze approach. It's amazing just how people are crazy enough to attempt it ! desparation I think.
The way I look it, hard disks are designed in such a way as to run hot, very hot. just put your hand on your drive that's been running for a few day's, you could almost fry an egg on it ! 

Freezing will contract the metal construction, of the drive internals. Therefore create more damage. Personally, I'd advise against it.

What about the way round ?

Let's say for instance, that your drive has a mechanical fault.
You're trying to boot a cold drive, the heads are stuck, it won't read. Why not heat the drive with a hair dryer, prior to booting ?

Anybody done that ?

---

### Post by dragonfly41 on 2012-02-02
Seems to me that this is surely no more desperate or crazy an idea than yours ..

> If I'm not mistaken, those are dry solder joints !
It so happens both drives have the same firmware versions, I have't  quite worked out the date codes as yet, I don't think that will matter  too much. My idea is to change the controller boards.More comment here ..

[http://lifehacker.com/comment/21676372/](http://lifehacker.com/comment/21676372/)

and argument _against_ trying this ...

[http://howto.wired.com/wiki/Save_Your_Hard_Drive_by_Freezing_It](http://howto.wired.com/wiki/Save_Your_Hard_Drive_by_Freezing_It)

---

### Post by WebNewbie on 2012-02-02
I seem to have it back to front ! bad diagnoses from my part.
Great article on the theory of freezing a hard drive. After all, the guy does have 15 years of experience in data recovey.
I hadn't taken into account the wear & tear on an old drive.
Internals don't get 'choked up', they get loose !

---

### Post by mips on 2012-02-02
> **WebNewbie said:**
> I seem to have it back to front ! bad diagnoses from my part.
Great article on the theory of freezing a hard drive. After all, the guy does have 15 years of experience in data recovey.
I hadn't taken into account the wear & tear on an old drive.
Internals don't get 'choked up', they get loose !

Don't! That might only help if you have something like stuck spindle motor with the cold shrinking the bearing.

You say the drive does not show up when connected to a SATA port? If that is correct then it might be related to a firmware issue.

So you can see the drive via USB but not when connected directly via a SATA interface? Have you tried a different SATA cable & interface?

---

### Post by WebNewbie on 2012-02-02
Hi **mips**, tried different sata cables and sata ports. I had the same problems unfortunately. So after work this evening, I resorted to plugging in my USB SATA adaptor and faulty drive. Installed my 1.5TB recovery drive internally. Booted to SystemRescueCD via USB PendriveLinux.

Booting took an eternity, I guess the system was looking for devices, and encountering difficulties. Had to abort.
So tried a different approach .....
Exact same setup, only this time, the USB adaptor was turned off. I waited for the boot process to complete, everything detected. Then I turned on the USB adapter.

Typed the command **df -h** in terminal, it still wasn't seen, so I mounted it.

The result is in the photo below.
*Sorry, had to take a photo of it, as SystemRescue doesn't have a screenshot utility in it.*

I will try to image the faulty drive now.

---

### Post by mips on 2012-02-03
> **WebNewbie said:**
> Hi **mips**, tried different sata cables and sata ports. I had the same problems unfortunately.

**When connected via SATA does the drive show up in the BIOS?**

---

### Post by WebNewbie on 2012-02-03
Hi **mips**, thanks for your patience.
No it wasn't seen in BIOS.

After the previous step. I unmounted the faulty drive, and made an image onto my 1.5TB drive using gddrescue. After about an hour, the procedure completed. I then checked the image, as I want to run the recovery from the image file. unfortunately, the image file was blank !

So, yet another approach, I connected my faulty drive via USB adaptor, to my windows PC, as I have 'RecoverMyFiles' installed on it. It detected the drive as RAW !

I then ran recover partition, which normally takes quite a few hours, went and did something else, but unfortunately, within two hours, my windows PC crashed :frown:

I'll try again tonight when I get home on a spare PC I have.

---

### Post by mips on 2012-02-03
> **WebNewbie said:**
> 
No it wasn't seen in BIOS.


Hang on then, that changes things. Will get back to you.

---

### Post by dragonfly41 on 2012-02-03
Re: your experiment with RecoverMyFiles

"Raw" files means unallocated ..

read more here

[http://www.recovermyfiles.com/data-recovery-help/drive-recovery-raw-disk.htm](http://www.recovermyfiles.com/data-recovery-help/drive-recovery-raw-disk.htm)

**[B]How to Recover a RAW, Unallocated or missing disk**[/B]
 Run Recover My Files and select "Recover a Drive" and click "Next".

---

### Post by WebNewbie on 2012-02-03
Hi **dragonfly41**, yeah, that was the procedure I was going through when my windows PC crashed !

Ref: RecoverMyFiles
Results of phase 1 - Partition Recovery
*Files found: 0
*File System Records: 0

RMF automatically goeas to Phase 2 - Scanning Blocks

This was the stage I had got to when my windows PC crashed.

In a earlier post, I said I would try that procedure again this evening when I get home, on a spare PC I have. But I have since then realised, it's a 64Bit machine. My version of RecoverMyFiles is a 32Bit program ! :mad:  damn !

---

### Post by dragonfly41 on 2012-02-03
I haven't tried this myself .. RStudio 64bit

[http://download.cnet.com/R-Studio-Data-Recovery-64-bit/3000-2094_4-75156809.html](http://download.cnet.com/R-Studio-Data-Recovery-64-bit/3000-2094_4-75156809.html)

---

### Post by mips on 2012-02-03
I doubt any software will work seeing you cannot see the drive from the BIOS. The USB controller is doing something really funny here and what it sees cannot be true.

I'll get back to you.

---

### Post by dragonfly41 on 2012-02-03
Remind us all if you have tried **testdisk** to recover partition table in unallocated partition

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)

Testdisk can be run from windows or ubuntu (on the external problem drive).

[COLOR=Navy]**TestDisk can:**
 
 * Fix partition table, recover deleted partition
 * Recover FAT32 boot sector from its backup
 * Rebuild FAT12/FAT16/FAT32 boot sector
 * Fix FAT tables
 * Rebuild NTFS boot sector
 * Recover NTFS boot sector from its backup
 * Fix MFT using MFT mirror
 * Locate ext2/ext3 Backup SuperBlock
 * Undelete files from FAT, NTFS and ext2 filesystem
 * Copy files from deleted FAT, NTFS and ext2/ext3 partitions. [/COLOR]


[http://www.x64bitdownload.com/downloads/t-64-bit-testdisk-photorec-download-ejvyrzrm.html](http://www.x64bitdownload.com/downloads/t-64-bit-testdisk-photorec-download-ejvyrzrm.html)
 
...

I did come across another thread which suggested editing BIOS (as per mips theory) but can't now find it.  But I dont know if your BIOS could have been affected with a power failure (which you said early in this thread occurred before this disk corruption)?

...

[COLOR=Navy][EDIT]

> 
"last_lba(): I don't know how to handle files with mode 40500"
Here's the thread ...

[http://www.linuxactionshow.com/forum/comments.php?DiscussionID=2349](http://www.linuxactionshow.com/forum/comments.php?DiscussionID=2349)

which suggests ..

> 
"Go into your bios and select Auto for the drive type, Block mode auto, dma auto, MBR protect off, virus protection off then save and reboot". 
[/COLOR]
[COLOR=Navy]
I don't really know if this is relevant to your scenario.  The common factor is the error message.[/COLOR]

---

### Post by WebNewbie on 2012-02-04
Hi all,

It's obvious to me that I will not be able to use my windows PC to run any sort of labour intensive tasks. As on one of my previous posts, informed you all of the system crash I had while running RecoverMyFiles. Can I just add at this point, RecoverMyFiles by GetData is an exceptional piece of software, saved my bacon many a time.

When I had the power outage, that damaged my drive with all my photos on, it must of damaged my motherboard also. As any task that envolves excessive CPU demands, my PC just shuts down ! Almost as if the temerature protection control, shuts down the PC, in order to protect an over heating CPU.

My original post, was a query related to disk imaging, as I was planning on imaging the faulty drive to a good 1.5TB drive, as at that time, I thought I had a failing drive. With all the help you guys have given, and links to various documentation that Google 'missed', I have now come to the conlusion, I have a damaged file system.

I currently have not run TestDisk directly on the faulty drive **dragonfly41**, as good practices tell you, 'treat your faulty disk as if it's the very last time it will run', you may never get another chance to recover your data from it.

Error 40500, seems to relate to a device detection problem, while looking at the boot process in BIOS ( switched off Quick Boot ), the BIOS info was, 4th IDE SMART capable but BAD.

**mips** said;
> I doubt any software will work seeing you cannot see the drive from the BIOS. The USB controller is doing something really funny here and what it sees cannot be true.

I think you may be right, that'll explain why I could see folders. The USB controlloers are just see a device, but it doesn't see data.

My next trial will be to run TestDisk directly on the faulty drive, as it seems the drives integrity is OK, and that it's a damaged file system. I will also attempt to repair the MBR, as PartImage has a MBR Repair utility. I understand that the NTFS file system keeps a backup of the MBR at the end of the disk, anyone ever tried to restore an MBR that way ?

---

### Post by WebNewbie on 2012-02-04
Sorry, replying to my own post .....

As my previous posts states;
> Error 40500, seems to relate to a device detection problem, while looking at the boot process in BIOS ( switched off Quick Boot ), the BIOS info was, 4th IDE SMART capable but BAD.



Found an article that recommends backing up all your data, as the drive is on it's way out !

---

### Post by dragonfly41 on 2012-02-04
An obvious question is whether you've tried data recovery where the failed disk (now in its USB enclosure) can be analysed on _another_ good working PC with appropriate 32 or 64 bit recovery program .. or trying testdisk first?  

This would eliminate the doubts about faulty motherboard, USB controller etc.

[EDIT 1]

The issue might be just recovery of damaged partition table so also investigate "partition table recovery" (which testdisk does).

[EDIT 2]

Further question.   Is your external USB drive separately powered or do you just rely on drawing power through USB port?

[EDIT 3]

If you're worried about using testdisk on your lost partition why not post your scenario to Christophe Grenier <grenier@cgsecurity.org> ?

Note that testdisk must be run with Administrator privileges.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery)

as in previous post.   Subscribe to testdisk forum.

---

