---
title: "How to use resync to backup"
date: 2011-03-27
forum: General Help
---

### Post by carusoswi on 2011-03-27
So, I figure it's high time I learn to use this utility (or something else, doesn't matter to me).  I want to backup a photo directory from an internal to external drive.

When I explore in Ubuntu, it names my external drive SimpleDrive . . . the destination directory on that drive I call Backup PhotoBank 31811.  I think I had a leading zero that Ubuntu drops for the date (031811).

My source drive is referred to by Ubuntu as 320 GB Filesystem, and the source directory on that drive is referred to as PhotoBank.

When I use these designations on the command line, rsync returns error messages stating that no such file or drive exists (note, I have not referenced any files within the directories).

If I click on properties for the 320 GB Filesystem, there is another name designated, a very long combination of numbers and letters.

I've tried using that name, but still get the same error messages from rsync.

What am I doing wrong?

Is there a front end for this program that is more graphical in nature?  I don't mind using the command line, as I know that once I get this sorted out, it should be no problem, but I'm not too proud to resort to the ultimate in simplicity.

I am seeking to copy the files from the internal one time, then, I plan to delete the files from the internal, load it back up, copy the new files to the external, and so forth.  I'm not really looking to sync the two drives.

Any suggestions most welcome.

Thanks.

Caruso

---

### Post by DeMus on 2011-03-27
With connected external drive look in your /media folder. Try to find the exact name of your drive.
Install Grsync and start it.
Write down the name of the internal drive and folder as written in the top line of the attached image, and the destination as on the second line. Choose the options. What I did works fine for me but maybe you want something else. Place your mouse over an option and read the help text which appears. Then execute.

Success.

---

### Post by carusoswi on 2011-03-27
> **DeMus said:**
> With connected external drive look in your /media folder. Try to find the exact name of your drive.
Install Grsync and start it.
Write down the name of the internal drive and folder as written in the top line of the attached image, and the destination as on the second line. Choose the options. What I did works fine for me but maybe you want something else. Place your mouse over an option and read the help text which appears. Then execute.

Success.

This looks to be exactly the sort of information for which I was looking.  Thank you for your quick and informative response.  I'm off to check out your suggestions.
Caruso

---

### Post by carusoswi on 2011-03-27
> **carusoswi said:**
> This looks to be exactly the sort of information for which I was looking.  Thank you for your quick and informative response.  I'm off to check out your suggestions.
Caruso

Ok, so, I tried Grsync, and, it seemed as though it might take all day before I started seeing any result from my backup, so, I had read earlier in the day that rsync only cares to work with linux partition types (not NTFS as this disc is formatted), so, I started up Gparted, have resized the NTFS (am shrinking it), to make room for an Ext3 partition.

The disc has a 1T capacity, of which only about 300 GB are currently in use.

Gparted reported a successful simulated resizing, but the actual process has been ongoing for a couple of hours,now.  I'm wondering if I should just let it continue to run or what.

The activity light on the disc is showing activity, which I suppose is a good thing, at least I'm working with the right volume.  I just am a bit surprised that it has taken this long.  I know that 300 GB of stuff is a lot to sort through, but was thinking that Gparted would not have to really work with that data in order to resize the partition and create a new one on the blank area of the disc.

I guess I am wrong about that.

Anyone else have this experience?

Thanks.

Caruso

---

### Post by carusoswi on 2011-03-27
> **carusoswi said:**
> Ok, so, I tried Grsync, and, it seemed as though it might take all day before I started seeing any result from my backup, so, I had read earlier in the day that rsync only cares to work with linux partition types (not NTFS as this disc is formatted), so, I started up Gparted, have resized the NTFS (am shrinking it), to make room for an Ext3 partition.

The disc has a 1T capacity, of which only about 300 GB are currently in use.

Gparted reported a successful simulated resizing, but the actual process has been ongoing for a couple of hours,now.  I'm wondering if I should just let it continue to run or what.

The activity light on the disc is showing activity, which I suppose is a good thing, at least I'm working with the right volume.  I just am a bit surprised that it has taken this long.  I know that 300 GB of stuff is a lot to sort through, but was thinking that Gparted would not have to really work with that data in order to resize the partition and create a new one on the blank area of the disc.

I guess I am wrong about that.

Anyone else have this experience?

Thanks.

Caruso

Three hours and counting.  We're still at task #1, resizing the partition.  Still have to create the EXT3 partition when that is finished.

I didn't really think that trying this might compromise my data on the 1T drive (although all of it is backup data, not crucial that it survive.

If this Gparted thing never ends, I may be forced to abandon the operation, which, I'm just guessing, may render the drive inaccessible without first formatting it.

I know this isn't the hottest of threads, but would appreciate any  advice (or consolation).

Caruso

---

### Post by oldfred on 2011-03-27
It really depends on where the data is on the drive. NTFS scatters parts all over and then you have to run defrag to clean it up. Gparted in effect has to move & verify all the data. I have heard of longer than over night depending on how much data. One reason I do not like very large partitions, but too small can also be a problem if they fill up and you have lots of room in another. Its a trade off.

If you stop gparted, you will more than likely damage file system. I would let it run.

---

### Post by carusoswi on 2011-03-27
> **oldfred said:**
> It really depends on where the data is on the drive. NTFS scatters parts all over and then you have to run defrag to clean it up. Gparted in effect has to move & verify all the data. I have heard of longer than over night depending on how much data. One reason I do not like very large partitions, but too small can also be a problem if they fill up and you have lots of room in another. Its a trade off.

If you stop gparted, you will more than likely damage file system. I would let it run.

I did let it run, Fred (fortunately had other chores to divert my attention like grilling our dinner, watching a bit of NCAA basketball).

It finally did finish after 4.5 hours.  I have spent the rest of the day trying to set permissions on that new partition so that I can use it to as a destination for backing up files.

I have spent quite a bit of time trying to locate something less than what appears Greek to me that I could type into the terminal to change ownership from root or to access root in order to set permissions to my user account so that I can make use of this storage space.

The simplest answer was found on this forum in the security section, a very short command by which I can temporarily raise my user privileges to give root access to most any GUI available to me in Ubuntu.  I raised Nautilus to root status, clicked to view the new drive's properties, clicked on the permissions tab, and set all permission options to read/write (or whatever Ubuntu calls these options, access/change or whatever).

At the risk of infuriating the mods, I must express my consternation as to why the permission thing is so strict.  I am not a formal IT guy, so, I'm guessing there is good reason.  On the other hand, for someone as persistent and determined as I, and, given the very open and helpful nature of this forum, finding the work around, while time consuming due to following searches that were less than productive or netted solutions I found too complex, finding a simple solution was not that big of a deal (thank you, moderators and forum leaders/contributors).

I want to read more about security so that I might develop a deeper understanding of why things are as they are in Ubuntu.  I have always been most appreciative of my relative freedom from viruses in Ubuntu, but, on the other hand, always a bit frustrated when prohibited from doing things that I feel should be very simple.

I know it's a trade-off, and, I guess, I must concede that I prefer erring on the side of caution at the expense of expediency, even if I do end up 'loosing' an afternoon to browsing/exploring for solutions to 'simple' issues.

FYI, with permissions loosed from their bonds, I have restarted Grsync, and it looks as though it will take as long to do an initial backup of my 297 GB of data as it took me to prepare the source partition.  This time, my diversion will be good old sleep.

Thanks to all who responded for your assistance.

I always know that, no matter the degree of my frustration, I will find useful answers here.

Caruso

---

### Post by oldfred on 2011-03-27
You can also use command line to set permissions & ownership. The basis of permission & ownership are fundamental to the security that Linux has. Windows makes everyone an admin and lets you read, write & execute everything. That allows virus and other damaging programs to run in the background. With Linux it has to ask, has to be in a folder that allows it to run etc.

A couple of scripts that automate the process. I use my version of MoutainX's but may add some of the first one's features.

Back to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh


Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by carusoswi on 2011-03-28
> **oldfred said:**
> You can also use command line to set permissions & ownership. The basis of permission & ownership are fundamental to the security that Linux has. Windows makes everyone an admin and lets you read, write & execute everything. That allows virus and other damaging programs to run in the background. With Linux it has to ask, has to be in a folder that allows it to run etc.

A couple of scripts that automate the process. I use my version of MoutainX's but may add some of the first one's features.

Back to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh


Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Hi, Fred, and thanks for responding.  Using that elevated Nautilus status, I succeeded in changing the permissions for the volume sdc2, and I Grsync has run since my last post (I did get some sleep, LOL), but, I come back to it, the bottom bar shows completion, but checking the location, no files were actually transferred.  It would appear that the folder I created via sudo on the command line is locked to my user account.  Apparently, I set permissions on the drive, but not that @#$%@$ folder.  It puzzles me because, I tested copy/delete before I started Grsync, but, perhaps I still had elevated privileges at that point.

I am going to give it another go, and will come back another day to explore and digest all your command line suggestions.  I do that analysis justice at 2:00 AM.  

I do appreciate your hanging in there with me, and I will likely be back with more questions as I start working through your links.  I do wish Rsync would communicate (sooner) when one sets it up in a way that will make it fail.

Caruso

---

### Post by carusoswi on 2011-03-28
> **carusoswi said:**
> Hi, Fred, and thanks for responding.  Using that elevated Nautilus status, I succeeded in changing the permissions for the volume sdc2, and I Grsync has run since my last post (I did get some sleep, LOL), but, I come back to it, the bottom bar shows completion, but checking the location, no files were actually transferred.  It would appear that the folder I created via sudo on the command line is locked to my user account.  Apparently, I set permissions on the drive, but not that @#$%@$ folder.  It puzzles me because, I tested copy/delete before I started Grsync, but, perhaps I still had elevated privileges at that point.

I am going to give it another go, and will come back another day to explore and digest all your command line suggestions.  I do that analysis justice at 2:00 AM.  

I do appreciate your hanging in there with me, and I will likely be back with more questions as I start working through your links.  I do wish Rsync would communicate (sooner) when one sets it up in a way that will make it fail.

Caruso

Totally PO'd at the moment.  A rerun of Grsync yielded yet another non-transfer of the subject files.

For me, this is totally unacceptable.  I set the parameters, set the permissions, and, yet, no backup.  I have already copied the subject files to another location. . . just wanted to perfect a proper backup.  I'll resort and stick to simple copying for now.  Doing a proper backup in Ubuntu is just too much work for me.

Later.

Caruso

---

### Post by carusoswi on 2011-03-29
> **carusoswi said:**
> Totally PO'd at the moment.  A rerun of Grsync yielded yet another non-transfer of the subject files.

For me, this is totally unacceptable.  I set the parameters, set the permissions, and, yet, no backup.  I have already copied the subject files to another location. . . just wanted to perfect a proper backup.  I'll resort and stick to simple copying for now.  Doing a proper backup in Ubuntu is just too much work for me.

Later.

Caruso

What a difference a day makes.  I used the elevated security method to which I referred above to start Grsync and tried a simulation.  The results were immediate.  I then ran the actual backup, and it is in progress as I type this.  I am still not certain why this extra security step should be required, but, at least I know it works.

Next on my agenda will be a thorough review of all things Ubuntu-security-related to see if I can sort out Ubuntu security in my head.

Thanks to everyone who offered assistance.

Caruso

---

### Post by carusoswi on 2011-03-29
One last observation:
rsync indicates that backup of this 297 gb of material will take about 25 minutes.  I could not resist trying to take a look at the contents of my destination folder, as I wondered if I would be able to actually observe the files as they populated the folder.  The folder will not open as it is locked, and I could not read any of its attributes (properties).

It will be interesting to see if this is a function of rsync having temporarily locked the folder during the backup or if it has something to do with my having raised the security level during the backup operation.  Only time (about 17 minutes,now) will tell.

Caruso

---

### Post by carusoswi on 2011-03-29
So, I see that the predictive time counter for rsync is much like my weather man . . . never wrong because the prediction is a moving target, updated as the 'weather' changes.

What was a 17 minute completion time has varied up and down.

My backup completion now sits at somewhere around 12 minutes, although it has remained around that number for the past 20 minutes.

In my last post, I mentioned that I had approximately 17 minutes to completion.  The program has now run some 75 minutes, and I still have 12 minutes, oops, make that 14 minutes left to go.

Since it is a backup, none of that really matters.  Percentage complete is at 85% and climbing steadily, and I can watch the files being copied via the Rsync output window.

I'm getting that warm feeling that all is working properly now.

Caruso

---

