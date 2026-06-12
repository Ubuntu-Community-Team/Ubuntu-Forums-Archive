---
title: "Back in time - restore after re-install"
date: 2010-09-12
forum: General Help
---

### Post by wbm on 2010-09-12
Hello,
I have my system and software and data on my computer on an internal drive.
On that system I have Back in Time backup software.
I use Back in Time, to backup my data to an external drive.

Question:
If my computer dies or my internal drive fails, I have to completely re-install everything including my system and Back in Time.
If I want to restore my data from the good external drive, how can I do that with Back in Time?
Doesn't it keep the Snapshots info or preferences on my dead drive? Or do I need to point my freshly re-installed Back in Time just to the data drive and it will recognize the snapshots etc. automatically?
I'd like to know this before anything happens please.
Thanks!!!

---

### Post by VastOne on 2010-09-12
> **wbm said:**
> Hello,
I have my system and software and data on my computer on an internal drive.
On that system I have Back in Time backup software.
I use Back in Time, to backup my data to an external drive.

Question:
If my computer dies or my internal drive fails, I have to completely re-install everything including my system and Back in Time.
If I want to restore my data from the good external drive, how can I do that with Back in Time?
Doesn't it keep the Snapshots info or preferences on my dead drive? Or do I need to point my freshly re-installed Back in Time just to the data drive and it will recognize the snapshots etc. automatically?
I'd like to know this before anything happens please.
Thanks!!!

Judging for the documentation [_[COLOR="SeaGreen"]here[/COLOR]_]("http://backintime.le-web.org/documentation/snapshots-dialog/") that is the case.  I am certain you would have to do some kind of re install of Ubuntu and Back-In-Time first and then point to the restore and proceed.

---

### Post by wbm on 2010-09-13
> **VastOne said:**
> Judging for the documentation [_[COLOR="SeaGreen"]here[/COLOR]_]("http://backintime.le-web.org/documentation/snapshots-dialog/") that is the case.  I am certain you would have to do some kind of re install of Ubuntu and Back-In-Time first and then point to the restore and proceed.

Sorry, but maybe I do not understand you correctly and maybe your link is incorrect.
It seems you just repeated what I said in my question,  and then show a link to the snapshot screenshots.

It would seem obvious that one would have to first re-install the system and Back in Time if one would want to use them.

My question is, will Back in Time be able to restore my Backups in the scenario I had outlined.

---

### Post by VastOne on 2010-09-13
> **wbm said:**
> Sorry, but maybe I do not understand you correctly and maybe your link is incorrect.
It seems you just repeated what I said in my question,  and then show a link to the snapshot screenshots.

It would seem obvious that one would have to first re-install the system and Back in Time if one would want to use them.

My question is, will Back in Time be able to restore my Backups in the scenario I had outlined.

Are you looking for a step by step how-to to guide you?

The docs and app seem pretty easy and straight forward, not too difficult to follow.

The only way to validate if it will work on your system is to test it and verify it and then you would trust it, I guess.

---

### Post by wbm on 2010-09-13
> **VastOne said:**
> Are you looking for a step by step how-to to guide you?

The docs and app seem pretty easy and straight forward, not too difficult to follow.

The only way to validate if it will work on your system is to test it and verify it and then you would trust it, I guess.

I could not find any documentation that actually addresses a worst case scenario. And that's really what backup is for, a worst case scenario.
All documentation I could find is about restoring lost or deleted or corrupt files from the same system that was used to create the backups. That does work great.
I don't think it would be reasonable to expect someone to trash his system just to find out if the backup software can restore data. I think that should be documented somewhere or be verified by someone who had the bad luck of system failure, but successfully restored his or her data after a complete system re-install with Back in Time.

---

### Post by VastOne on 2010-09-13
> **wbm said:**
> I could not find any documentation that actually addresses a worst case scenario. And that's really what backup is for, a worst case scenario.
All documentation I could find is about restoring lost or deleted or corrupt files from the same system that was used to create the backups. That does work great.
I don't think it would be reasonable to expect someone to trash his system just to find out if the backup software can restore data. I think that should be documented somewhere or be verified by someone who had the bad luck of system failure, but successfully restored his or her data after a complete system re-install with Back in Time.

Having worked in disaster recovery for many many years I can tell you that no two companies data is exact and the education and success comes in creating a duplicate environment (usually a bunker) and testing testing testing.

It is really the only way to guarantee your data.  In my test environments I have several machines that I routinely break to test the restore functions to my environment, including Back-In-Time.

I can tell you that it works as advertised for me, but that may not mean anything at all to your what you are running and to what is important to you. It is all subjective.

---

### Post by wbm on 2010-09-13
> **VastOne said:**
> Having worked in disaster recovery for many many years I can tell you that no two companies data is exact and the education and success comes in creating a duplicate environment (usually a bunker) and testing testing testing.

It is really the only way to guarantee your data.  In my test environments I have several machines that I routinely break to test the restore functions to my environment, including Back-In-Time.

I can tell you that it works as advertised for me, but that may not mean anything at all to your what you are running and to what is important to you. It is all subjective.

Can you back up data from one machine and the restore it from a different machine with Back in Time? I guess that would be the simplest way of putting it.
If yes, how do permission play into this? Would both machines have the same user name/passwords for this to work flawlessly?
Thanks. It looks like you have done your homework in that regard pretty well.

---

### Post by VastOne on 2010-09-13
> **wbm said:**
> Can you back up data from one machine and the restore it from a different machine with Back in Time? I guess that would be the simplest way of putting it.
If yes, how do permission play into this? Would both machines have the same user name/passwords for this to work flawlessly?
Thanks. It looks like you have done your homework in that regard pretty well.

Yes, I have done that but keep in mind, in my restores, I keep the user names and locations identical for simplistic reasons and not have to worry about permissions.  I also have a separate /Home directory that maintains all of my settings and that is a separate backup process.  And I have the data backed up on multiple media and device formats at another location in the event of a catastrophic disaster (fire, flood, tornado etc etc)

This by default is the concept behind disaster recovery, getting back to where you were as quickly as possible.

---

### Post by wbm on 2010-09-13
> **VastOne said:**
> Yes, I have done that but keep in mind, in my restores, I keep the user names and locations identical for simplistic reasons and not have to worry about permissions.  I also have a separate /Home directory that maintains all of my settings and that is a separate backup process.  And I have the data backed up on multiple media and device formats at another location in the event of a catastrophic disaster (fire, flood, tornado etc etc)

This by default is the concept behind disaster recovery, getting back to where you were as quickly as possible.

I have tried Back in Time like this:
2 computers with same user names and passwords

Computer 1: run Back in Time and Backup a bunch of folders to and external drive. E.g. Music, Pictures, Videos

go to computer 2

Computer 2: install Back in Time, and launch it. How do I get my data back? Before it even lets me navigate to my snapshots to restore, I have to tell it where to store my snapshots and which directories I want to include.
As far as I can tell, unless I set it up exactly as it was on computer 1, I cannot get my data back easily. That would mean that I can only restore what I remember I had included on computer 1.
In my test, I then also could not restore more than 1 folder or 1 item at a time. I could not e.g. restore the entire "music" folder I had specified as an "Include" folder.

Maybe I do need a step by step, but I don't see an easy way of pointing the software to a "Snapshot" and restoring my folder structure after a complete system re-install.

---

### Post by tgm4883 on 2010-09-13
> **wbm said:**
> I have tried Back in Time like this:
2 computers with same user names and passwords

Computer 1: run Back in Time and Backup a bunch of folders to and external drive. E.g. Music, Pictures, Videos

go to computer 2

Computer 2: install Back in Time, and launch it. How do I get my data back? Before it even lets me navigate to my snapshots to restore, I have to tell it where to store my snapshots and which directories I want to include.
As far as I can tell, unless I set it up exactly as it was on computer 1, I cannot get my data back easily. That would mean that I can only restore what I remember I had included on computer 1.
In my test, I then also could not restore more than 1 folder or 1 item at a time. I could not e.g. restore the entire "music" folder I had specified as an "Include" folder.

Maybe I do need a step by step, but I don't see an easy way of pointing the software to a "Snapshot" and restoring my folder structure after a complete system re-install.

I've been messing with backintime looking for a good backup solution and I can tell you that is not the case. Backintime seems to be the best backup/restore solution (excluding things like bacula and amanda). It seems to me that all of the backup information is kept in the backup folder, not on a host machine. This would indicate that for a complete restore, you would need to.

1) Reinstall Ubuntu
2) Reinstall Backintime
3) Point Backintime to your usb drive backup folder
4) Tell backintime to restore your data. If you restore a higher level folder it will restore all subfolders. (eg. If you had previously backed up /home/thomas, then all subfolders of /home/thomas are backed up as well. To restore, all you should need to do is select /home/thomas and select restore)

To make things a little more complicated, there may be permissions issues if the UID of the old user and new user don't match. I haven't tested that yet.

---

### Post by wbm on 2010-09-13
> **tgm4883 said:**
> I've been messing with backintime looking for a good backup solution and I can tell you that is not the case. Backintime seems to be the best backup/restore solution (excluding things like bacula and amanda). It seems to me that all of the backup information is kept in the backup folder, not on a host machine. This would indicate that for a complete restore, you would need to.

1) Reinstall Ubuntu
2) Reinstall Backintime
3) Point Backintime to your usb drive backup folder
4) Tell backintime to restore your data. If you restore a higher level folder it will restore all subfolders. (eg. If you had previously backed up /home/thomas, then all subfolders of /home/thomas are backed up as well. To restore, all you should need to do is select /home/thomas and select restore)

To make things a little more complicated, there may be permissions issues if the UID of the old user and new user don't match. I haven't tested that yet.

The problem is:
3) Point Back in Time to ...
Exactly how would one do that? As far as I can tell one has to do a bunch of steps as outlined in my previous post before one can do that.
It would be nice and the obvious choice though if it would actually work the way you describe it.

Also,
4) as far as I can tell you cannot restore something unless you set up your "include" folders first to match what you want to restore.

---

### Post by VastOne on 2010-09-13
> **wbm said:**
> The problem is:
3) Point Back in Time to ...
Exactly how would one do that? As far as I can tell one has to do a bunch of steps as outlined in my previous post before one can do that.
It would be nice and the obvious choice though if it would actually work the way you describe it.

Also,
4) as far as I can tell you cannot restore something unless you set up your "include" folders first.

You have to establish access to the files on the drive by either taking it to the 2nd computer and connecting it (easy way) or by establishing a network connection and then ssh or samba (harder way and slower)

You must realize that you need the snapshot available to the 2nd computer

---

### Post by tgm4883 on 2010-09-13
> **wbm said:**
> The problem is:
3) Point Back in Time to ...
Exactly how would one do that? As far as I can tell one has to do a bunch of steps as outlined in my previous post before one can do that.
It would be nice and the obvious choice though if it would actually work the way you describe it.

Also,
4) as far as I can tell you cannot restore something unless you set up your "include" folders first to match what you want to restore.

I'll test this some more when I get home, but I believe all of that information is kept in the backintime backup folder that would be residing on your external drive. All you should have to do is point backintime at that folder.

---

### Post by VastOne on 2010-09-13
[_[COLOR="DarkOrange"]This[/COLOR]_]("http://www.oak-tree.us/blog/index.php/2009/07/20/back-in-time1") is the best how to on Back-In-Time that I have located.

Note his limitation at the end:

> But even though Back In Time is probably the best user-oriented backup solution I’ve found for Linux, it still isn’t perfect.  (Though really, really close.)  There is at least one major limitation: lack of a network based backup.

This can be over come by establishing a network connection either from the backup procedure by backing it up to the 2nd computer (via a network connection to that computer) or by connecting to the 1st computer via a network connection and accessing the snapshots.

My main Ubuntu /Root is small enough (with the correct exclusions)  snapshot to fit on a 8 gig thumb drive and all I do is copy it to the restore machine and work from there.

For my bigger areas, /Home and a mount that has all my music and critical files, I use grsync and do a nightly sync of those to the 2nd computer using an ssh connection.  For those, the first time you sync is the longest since it takes all the data over, but after that it is very small as only the incremental changes are copied over.

---

### Post by wbm on 2010-09-13
> **VastOne said:**
> [_[COLOR="DarkOrange"]This[/COLOR]_]("http://www.oak-tree.us/blog/index.php/2009/07/20/back-in-time1") is the best how to on Back-In-Time that I have located.

Note his limitation at the end:



This can be over come by establishing a network connection either from the backup procedure by backing it up to the 2nd computer (via a network connection to that computer) or by connecting to the 1st computer via a network connection and accessing the snapshots.

My main Ubuntu /Root is small enough (with the correct exclusions)  snapshot to fit on a 8 gig thumb drive and all I do is copy it to the restore machine and work from there.

For my bigger areas, /Home and a mount that has all my music and critical files, I use grsync and do a nightly sync of those to the 2nd computer using an ssh connection.  For those, the first time you sync is the longest since it takes all the data over, but after that it is very small as only the incremental changes are copied over.

The review is nice to start backing up, but it does not address my question at all. Just like all other tutorials I have seen, it does not deal at all with the most important aspect of backup, how to get the data back after the system has failed and the system, and Back in Time has been re-installed.

---

### Post by VastOne on 2010-09-13
> **wbm said:**
> The review is nice to start backing up, but it does not address my question at all. Just like all other tutorials I have seen, it does not deal at all with the most important aspect of backup, how to get the data back after the system has failed and the system, and Back in Time has been re-installed.

You have to understand that there is no real way to "show" the restore process because everyone's restore process is different with different data, locations, requirements etc etc etc.

I am not sure what you are really wanting as I have tried to outline it for you and have shown sites that highly recommend it.  There is no hand holding procedure in this area of recovery as it is very subjective to what your data and setup is.

All I can tell you is I have used it the way I have explained it. Doing it the way I have explained works for me and my data and my sanity is secure.

The restore process was simply selecting the snapshot and then pointing it to where I wanted it restored, a very simple 2 step process.

---

### Post by wbm on 2010-09-13
> **tgm4883 said:**
> I'll test this some more when I get home, but I believe all of that information is kept in the backintime backup folder that would be residing on your external drive. All you should have to do is point backintime at that folder.

Let me know what you find. I thought the same as you and was very (unpleasantly) surprised that it's not that simple. It actually seems to be quite a pain if you have multiple folders you are backing up.
It appears to me that one has to do the following:
1. re-install system with same user names and passwords
2. install Back in Time
3. configure Back in Time the exact same way as it was on the previous system, e.g. point it to the same Snapshot location and establish the same "include" folders.

If you do that, it looks like all is well.
The problem is if you do not remember ALL your Back in Time settings and/or ALL your "include" folders. Then it gets iffy.

Lastly, once you configured all your settings exactly as in your previous install, you should probably restore first before you create a new snapshot.
Unless I am seriously missing something here, all this seems to be a very convoluted and dangerous way of backing up and restoring data.
I hope I am missing something here :)

---

### Post by tgm4883 on 2010-09-13
> **wbm said:**
> The review is nice to start backing up, but it does not address my question at all. Just like all other tutorials I have seen, it does not deal at all with the most important aspect of backup, how to get the data back after the system has failed and the system, and Back in Time has been re-installed.

As said before, it is difficult to explain. As with all backup/restore processes, you need to test it. I believe that if you created a virtual machine and tried a restore you would see how easy it is and why each step isn't documented. It's pretty intuitive

---

### Post by wbm on 2010-09-13
> **tgm4883 said:**
> As said before, it is difficult to explain. As with all backup/restore processes, you need to test it. I believe that if you created a virtual machine and tried a restore you would see how easy it is and why each step isn't documented. It's pretty intuitive

I did that and it did not work easily. Please see my above post.
I set up Ubuntu 10.04 in VBox ran Back in Time
Then I moved to a different install of Ubuntu 10.04, installed Back in Time and had to go through all the hoops I mentioned in my previous post to get my data back.

---

### Post by tgm4883 on 2010-09-13
> **wbm said:**
> I did that and it did not work easily. Please see my above post.
I set up Ubuntu 10.04 in VBox ran Back in Time
Then I moved to a different install of Ubuntu 10.04, installed Back in Time and had to go through all the hoops I mentioned in my previous post to get my data back.

Ok, so not 100% intuitive, but not that difficult either.

*) You do have to set up a backup folder when you are going to restore, and what to backup (last part doesn't make sense)

*) Once you do, all you have to do is right click on the data you want to restore and select restore. If you previously backed up information from an area you don't have access to, you will need to run backintime as root (from the menu)

I just tested this from my host OS to a new VM. All i did was zip up teh backintime folder and move it to the VM. I even unzipped the backintime folder to a different directory on the VM. When I told it to restore the media folder, it restored the folder and all sub items (though I did have to run backintime as root).

That seems pretty simple and except for the part where I had to set up a backup folder first was pretty intuitive (although I can see why this is necessary, backintime needs to know where the snapshots are, this part could probably be explained better in the GUI)

---

### Post by VastOne on 2010-09-13
> **tgm4883 said:**
> Ok, so not 100% intuitive, but not that difficult either.

*) You do have to set up a backup folder when you are going to restore, and what to backup (last part doesn't make sense)

*) Once you do, all you have to do is right click on the data you want to restore and select restore. If you previously backed up information from an area you don't have access to, you will need to run backintime as root (from the menu)

I just tested this from my host OS to a new VM. All i did was zip up teh backintime folder and move it to the VM. I even unzipped the backintime folder to a different directory on the VM. When I told it to restore the media folder, it restored the folder and all sub items (though I did have to run backintime as root).

That seems pretty simple and except for the part where I had to set up a backup folder first was pretty intuitive (although I can see why this is necessary, backintime needs to know where the snapshots are, this part could probably be explained better in the GUI)

Perhaps I have never seen this issue because I have always kept the backup/snapshot location the same on both machines and when I first install Back In Time I tell it this location.  From there all I have had to do is right click on the snapshot and proceed with the restore.

---

### Post by tgm4883 on 2010-09-13
> **VastOne said:**
> Perhaps I have never seen this issue because I have always kept the backup/snapshot location the same on both machines and when I first install Back In Time I tell it this location.  From there all I have had to do is right click on the snapshot and proceed with the restore.

I'd bet you set an include directory as well.

---

### Post by VastOne on 2010-09-13
> **tgm4883 said:**
> I'd bet you set an include directory as well.

Yes that is affirmative.

---

### Post by VastOne on 2010-09-13
> **wbm said:**
> The review is nice to start backing up, but it does not address my question at all. Just like all other tutorials I have seen, it does not deal at all with the most important aspect of backup, how to get the data back after the system has failed and the system, and Back in Time has been re-installed.

If you want to know the complete process involved here, I would highly recommend that you learn everything you can about rsync.

BackInTime and Grsync are both just GUI shells for rsync underneath the hood.

Another very good backup and restore process involving drives is dd, one you would really need to understand before attempting.

Also, the tar method is another good I have used successfully.

---

### Post by keypox on 2010-09-14
I have been looking for the same thing as the OP.  

I have been trying to clone my install using remastersys.  To make a Dist iso, then use backintime or deju dup, or something to back up the rest.

Remastersys also has a full backup solution.  But from everything i have read you will not get a clone, you will have permissions problems and UUID problems. 

I think using remastersys with the dist option. And making /home on a seperate partition.  Then if you need to reinstall, without HD failer, you cna just reinstall using the dist iso, which will restore all your programs, and then your /home would have all your settings and personal files.  

The remastersys dist iso, did work in a VM and had all my programs, and repos.  But I have not tested, or tried to backup my home and see it would be the exact same. In theory it should...

See here for more info 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by VastOne on 2010-09-14
> **keypox said:**
> I have been looking for the same thing as the OP.  

I have been trying to clone my install using remastersys.  To make a Dist iso, then use backintime or deju dup, or something to back up the rest.

Remastersys also has a full backup solution.  But from everything i have read you will not get a clone, you will have permissions problems and UUID problems. 

I think using remastersys with the dist option. And making /home on a seperate partition.  Then if you need to reinstall, without HD failer, you cna just reinstall using the dist iso, which will restore all your programs, and then your /home would have all your settings and personal files.  

The remastersys dist iso, did work in a VM and had all my programs, and repos.  But I have not tested, or tried to backup my home and see it would be the exact same. In theory it should...

See here for more info 
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

An even easier way is by having /Home on one partition (always backed up), a Distro iso install disk  and having your current install applications in a txt file.

Backup your current installed packages (Applications) by doing this:

Applications

Make a list of your current applications by running this in terminal

```
sudo dpkg --get-selections > /home/your user name here/applications.txt
```  

Always keep an up to date and safe copy of this file


Restore

Once your done with the new install of Ubuntu, copy the file applications.txt into your home directory (it will already be there if you have restored your /home). 

You also want to make sure you have all the same source.list that you had in your previous installation, especially if you use ppa's to get software that is not in the normal repositories.  You would just need to add the same ppa's to your current install source.list the same way you added them before.

Once you know it is there run this

```

sudo dpkg --set-selections /home/applications.txt && apt-get dselect-upgrade
```

apt-get will now start downloading all your apps, this will take some time depending on the number of apps you have installed.


In following this, your new installation would have all your settings (saved in /Home) and all your apps installed, thus getting you back to where you were.

I use this method quite frequently to get the daily builds installed.

This command solves uuid issues when using remastersys or dd.

```
sudo tune2fs -U random /dev/sdax 
``` 

where x is the sda device in question

---

