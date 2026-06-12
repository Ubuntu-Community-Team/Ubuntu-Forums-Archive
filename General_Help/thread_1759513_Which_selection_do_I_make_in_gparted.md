---
title: "Which selection do I make in gparted?"
date: 2011-05-15
forum: General Help
---

### Post by ClientAlive on 2011-05-15
I'm ready to push the button on this baby right now -  :)


I just need to know which selection in that drop down list will lead me to being able to make the ext4 filesystem. Picture attached.

Thanks guys.

---

### Post by Hedgehog1 on 2011-05-15
For your purposes, the MSDOS partition map is fine.

You will actually set the format type of ext4 in the partition setup itself:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

***The Hedge***

:KS

---

### Post by ClientAlive on 2011-05-15
> **Hedgehog1 said:**
> For your purposes, the MSDOS partition map is fine.

You will actually set the format type of ext4 in the partition setup itself:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

***The Hedge***

:KS


Thanks Hedge. I keep seeing you show up to rescue me.  :D

So I have two simple questions before I "push the button" on this thing:

1) If I format the entire drive it will be usable right? It's an external usb drive. I mean, it doesn't have some boot thing on it that it needs does it?

2) the . . .

>  / 

is the correct selection for "boot from" ??

Thanks Hedgehog1
----------------------

Edit: Nevermind (2) I see in your pics you are showing me that. What about (1) though?

---

### Post by srs5694 on 2011-05-16
Hedgehog1 is showing screen shots from a different utility than you're using, ClientAlive. Yours appears to be from GParted, whereas Hedgehog1 seems to be showing the Ubuntu installer. GParted doesn't ask about mount points, so you won't set those in GParted. Instead, Ubuntu will probably auto-mount the partition(s) you create in a subdirectory of /media.

I recommend more precision in discussing the issue. The word "format" is hopelessly vague, and it's unclear which of at least three meanings is intended for most of the uses in this thread. There are in fact three distinct operations being performed (or at least contemplated), in sequence:


[list=1]
[*]**Creating a partition table** -- Most disks use a *partition table*, which is a relatively simple data structure that describes how a disk is carved up. For instance, sectors 2048 to 204799 are partition 1, sectors 204800 to 799999 are partition 2, and so on. This data structure must be created to start the process. That's what the dialog box you showed in your screen shot is asking about, ClientAlive. There are several different partition table formats available, the most common being the Master Boot Record (MBR; aka "msdos") and the GUID Partition Table (GPT). If you expect to use the disk on another computer or from another OS, MBR is the safest choice; however, GPT has some advantages and is preferable in some cases, such as when you're booting from the disk on a computer that's based on EFI or UEFI firmware. Since this is an external disk, though, Hedgehog1's advice to use MBR is probably appropriate. Note, however, that your disk already has a partition table -- otherwise the NTFS partition you can make out in the screen shot wouldn't be present. Note also that, as the dialog box warns, creating a new partition table will render your old partition(s), and the data on them, inaccessible. So do this only if you're certain you don't need any data on that drive!
[*]**Creating partition(s)** -- Once the partition table has been created, you can create partition(s) in that partition table. Alternatively, instead of creating a completely new partition table, you could delete the existing partition(s) (or just some of them, if the disk has several) and create one or more new partition(s). If you want to completely wipe all the data from the disk, either approach is fine. Both operations are very quick. So is creating partitions; writing the partition data structures takes a fraction of a second.
[*]**Creating filesystem(s)** -- A *filesystem* is a data structure that normally resides inside a partition. It helps the computer store and access files. Filesystems are much more complex than partition tables. If you create a filesystem in a partition, the partition's contents will be lost. In your case, if you want to replace all the data on the disk, you could just create a new filesystem over the existing partition. Creating a filesystem usually takes between a fraction of a second and a few seconds, depending on the filesystem and the partition's size.
[/list]


Many tools, including GParted, merge the partition creation and filesystem creation steps; you tell them you want to create a partition of a particular size and a certain filesystem type, and the tool does both things in sequence, thus blurring the line (in the user's mind) between the two steps; but they really are different things.

It's impossible to say with certainty which of these things you need to do, since you haven't said what you intend to do with the disk. If you intend to keep current data on the disk, though, you definitely should not do #1, and you might need to do other things (like resize or move partitions) that aren't in that list. If you want to wipe all the data on the disk and use it exclusively with ext4fs from Linux, you could do #3 alone, #2 and #3 (after deleting the current partition(s), or #1, #2, and #3. The end results will be indistinguishable for all three courses of action, unless there's something odd about the partition(s) on there now or that you create, or unless you change the partition table type. Even in these cases, the differences are likely to be very subtle, like a usable filesystem size that differs by a few kilobytes.

---

### Post by ClientAlive on 2011-05-16
> **srs5694 said:**
> Hedgehog1 is showing screen shots from a different utility than you're using, ClientAlive. Yours appears to be from GParted, whereas Hedgehog1 seems to be showing the Ubuntu installer. GParted doesn't ask about mount points, so you won't set those in GParted. Instead, Ubuntu will probably auto-mount the partition(s) you create in a subdirectory of /media.

I recommend more precision in discussing the issue. The word "format" is hopelessly vague, and it's unclear which of at least three meanings is intended for most of the uses in this thread. There are in fact three distinct operations being performed (or at least contemplated), in sequence:


[list=1]
[*]**Creating a partition table** -- Most disks use a *partition table*, which is a relatively simple data structure that describes how a disk is carved up. For instance, sectors 2048 to 204799 are partition 1, sectors 204800 to 799999 are partition 2, and so on. This data structure must be created to start the process. That's what the dialog box you showed in your screen shot is asking about, ClientAlive. There are several different partition table formats available, the most common being the Master Boot Record (MBR; aka "msdos") and the GUID Partition Table (GPT). If you expect to use the disk on another computer or from another OS, MBR is the safest choice; however, GPT has some advantages and is preferable in some cases, such as when you're booting from the disk on a computer that's based on EFI or UEFI firmware. Since this is an external disk, though, Hedgehog1's advice to use MBR is probably appropriate. Note, however, that your disk already has a partition table -- otherwise the NTFS partition you can make out in the screen shot wouldn't be present. Note also that, as the dialog box warns, creating a new partition table will render your old partition(s), and the data on them, inaccessible. So do this only if you're certain you don't need any data on that drive!
[*]**Creating partition(s)** -- Once the partition table has been created, you can create partition(s) in that partition table. Alternatively, instead of creating a completely new partition table, you could delete the existing partition(s) (or just some of them, if the disk has several) and create one or more new partition(s). If you want to completely wipe all the data from the disk, either approach is fine. Both operations are very quick. So is creating partitions; writing the partition data structures takes a fraction of a second.
[*]**Creating filesystem(s)** -- A *filesystem* is a data structure that normally resides inside a partition. It helps the computer store and access files. Filesystems are much more complex than partition tables. If you create a filesystem in a partition, the partition's contents will be lost. In your case, if you want to replace all the data on the disk, you could just create a new filesystem over the existing partition. Creating a filesystem usually takes between a fraction of a second and a few seconds, depending on the filesystem and the partition's size.
[/list]


Many tools, including GParted, merge the partition creation and filesystem creation steps; you tell them you want to create a partition of a particular size and a certain filesystem type, and the tool does both things in sequence, thus blurring the line (in the user's mind) between the two steps; but they really are different things.

It's impossible to say with certainty which of these things you need to do, since you haven't said what you intend to do with the disk. If you intend to keep current data on the disk, though, you definitely should not do #1, and you might need to do other things (like resize or move partitions) that aren't in that list. If you want to wipe all the data on the disk and use it exclusively with ext4fs from Linux, you could do #3 alone, #2 and #3 (after deleting the current partition(s), or #1, #2, and #3. The end results will be indistinguishable for all three courses of action, unless there's something odd about the partition(s) on there now or that you create, or unless you change the partition table type. Even in these cases, the differences are likely to be very subtle, like a usable filesystem size that differs by a few kilobytes.


Thank you for clarifying. In the meantime, before your response, I went ahead and attempted to do what I was trying to do. I'm pretty certain the steps I took were the correct ones for my purpose but I ended up getting an error message from gparted and the job was never completed. From those error messages I believe what may have happened is some things (perhapst the partition table?) were removed but it stopped short of creating the file system. I will attach those error messages with this post.

Here's what I was trying to do.

I have a 232.88 GB external usb drive plugged into this computer. It is formatted in ntfs (from my windows days before coming to Linux). I no longer care about the data this is on the disk and would like to (pave over?) it with the ext4 file system type. The disk is also encrypted (the entire disk space) with a program called Cypherix (a program I purchased when still using windows). Cypherix only works with Windows and I am no longer using Windows. I'm on Linux now. The person at the Cyperix web site told me in chat that it is possible to format the disk and it would erase everything and remove the encryption. That's what I was trying to do and here are the steps I took:

> 
Device > Create Partition Table

 Then, in the window that pops up (the one pictured in post #1), selected:

 "msdos" in the drop down list

 Then, in the main widow, after selecting the drive:

 Partition > New

Then selected "Primary Partition" for the "Create As" field and "ext4" for the "File System" field.

Then clicked "Add"

Then, after making sure the drive is selected in the main window:

 Edit > Apply All Operations


 I then got the error message I've attached (name ending "_01")

 Then I tried to run it again (a second time) the same way (identical to the above listed steps). I then got the error message attached (name ending "_02") - which is slightly different ( I think).



As it stands at this moment I'm afraid to unmount the thing for fear it is somehow, like, half-baked and won't mount again to be able to complete the goal.

Error messages attached.

I have also attached two pictures. The one titled "selections" shows exactly how I had things set up before clicking "Add". The other titled "current_status" shows where things sit at this moment. Notice that in the bar across the top of the main window in the file titled "current_status") it shows the entire space as being unallocated space - for the entire size of the disk. This is not how that bar read when I first launched gparted. That way it was when I started is all but about a gig and a half was used space - and it reflected that in that bar. This is a difference and is what worries me about unmounting this thing without finishing this out.

This disk is currently plugged into my computer and on/ running. I intend to let it remain so until this is resolved. Unfortunately I must go to bed now and may not be free again to deal with this until tomorrow afternoon. I will check back here when I wake though and will do what I have time to before leaving for work.

What do I do? Someone I talked to said to unmount it first using "umount". That didn't make sense or even seem to apply to what I'm trying to do.

As a side note: when looked at this disk in nautilus (after the first run and first error message) everything appeared as it did before I began. I still see the folders that were there before. For what it's worth though I don't trust that to mean it's safe to unmount it. Just because I can see a couple file folder icons with names may not mean much at all under the circumstances.

---

### Post by ClientAlive on 2011-05-16
The disk contains media and documents I no longer care to keep.

In a nutshell, what I wanted to end up with is on big blank disk that I could begin to use again.

I will most likely be using this disk, primarily, to store media again (such as movies and music).

One decision I faced had to do with the fact that I may want to share/ watch/ listen to one or more of them with a friend at some point in the future. I'm told that Linux can read and use ntfs but I don't want to deal with file system corruption known to be an issue with ntfs. I had decided tonight to go with ext4 with the notion that anything I may want to use on a Windows system could be copied over to my flash/ thumb drive and transported in that way.

Again, the disk is encrypted with Cypherix (but I'm told by them I can format over it). Cypherix only works on Windows. I would have dealt with this before switching my system to Linux but didn't have anywhere to park that much data; and, at the time, I believed I wanted to keep it. I have since changed my mind.

The only reason I didn't try to do this from the command line, using the tools already available, is that I was afraid of specifying the wrong disk somehow and erasing my system/ local disk.

Just thought I would try and clarify.

If anyone can help me do this the right way I would really appreciate it. I know, from learning it the hard way, that Linux doesn't care and one can easily dig themselves a deeper hole. That is not what I would llke to see happen here.

---

### Post by nothingspecial on 2011-05-16
If the guy at Cypherix said you can format it then format it.

It seems that every disc you buy nowadays comes with all kinds of encryption/backup windows software. I just plug it in and format it.

Btw, you will have to unmount it before you do because you cannot format a mounted drive.

---

### Post by ClientAlive on 2011-05-16
> **nothingspecial said:**
> If the guy at Cypherix said you can format it then format it.

It seems that every disc you buy nowadays comes with all kinds of encryption/backup windows software. I just plug it in and format it.

Btw, you will have to unmount it before you do because you cannot format a mounted drive.


Attached is a text file of the transcript emailed to me by Cypherix.

However, the position I am in is described in my previous post. I'm at a dead end. gparted does not seem to want to create this file system for me.

---

### Post by nothingspecial on 2011-05-16
Is that because it is still mounted?

Like I said, you cannot format a mounted file system........

......and as such (unless you are using a live cd) you cannot format your system.

However you can still format other unmounted partitions, so take care.

---

### Post by ClientAlive on 2011-05-16
> **nothingspecial said:**
> Is that because it is still mounted?

Like I said, you cannot format a mounted file system........

......and as such (unless you are using a live cd) you cannot format your system.

However you can still format other unmounted partitions, so take care.


I'm sorry nothingspecial I dadn't cought that. How could one possibly format an unmounted disk though? If it is unmounted the system will not recognize it's existence right?

Now I remember reading something like this. Well, that gparted can be run live from a usb stick. So then that's the only way? I can try that . . .

Thanks and sorry again man. Sorry everyone if I sounded a little snippy. I was a little frustrated over this last night and kept worrying something was gonna happen to this thing that would make it unusable.

---

### Post by nothingspecial on 2011-05-16
Being unmounted is not the same as being unplugged.

Of course you can't format a partition that isn't physically connected to the system.

But you need to unmount it before you do.

Click eject (or unmount, or safely remove) or whatever it says before you format it.

I wouldn't do it from a live usb because that way you can make a mistake and wipe your system.

---

### Post by srs5694 on 2011-05-16
I *suspect* that what happened is that your disk was mounted prior to your doing anything with GParted. Then when you created the new partition table, the disk was still mounted, using data in the old partition table cached by the kernel. (I just tried this and GParted wouldn't let me create a new partition table; but perhaps you're using an older version that lacks such a check.) Now you've created a new partition table and the software is getting confused by the combination of the old and new data.

You can probably get around this by exiting from GParted and typing the following command in a Terminal window:

```

sudo umount /dev/sdb1

```

Note that the command name is "umount", not "unmount" (it's missing the first "n"). If that works, I recommend then using GParted to create *another* fresh partition table. If unmounting the partition doesn't work, the easiest solution is to reboot the computer. (It'd be more elegant to properly diagnose the problem, but that would take too long to explain how to do.)

You do *not* need to boot from a recovery disc to resolve this problem. That's necessary when you want to operate on a partition that you can't unmount in other ways, such as your main Linux root (/) partition; but this is an external non-boot disk that you can unmount and leave Linux running, so you can use the main system to operate on the removable disk.

One more point: Given your needs, I might consider either of two other filesystems rather than ext4fs:


[list]
[*]**FAT** -- This old standby is accessible by everything, so you can unmount and unplug the disk from Linux, move it to another computer, and access all its files. Its biggest drawback in your case is probably its 4 GiB file size limit; it sounds like you might be storing multimedia files on the disk, in which case 4 GiB may be too limiting.
[*]**ext3fs** -- This predecessor to ext4fs is better supported outside of Linux than is ext4fs. Thus, you'll have a better chance of accessing the disk from a Windows system by installing appropriate drivers than would be the case if you used ext4fs. Ext4fs adds a number of features, but the most important of these relate to support for large hard disks and large files (in the terabyte range and over). It's also got some speed improvements, but for the most part you're not really getting all that much extra by going from ext3fs to ext4fs on a disk of your size.
[/list]


You could also use two partitions on the disk -- for instance, a smallish FAT partition along with a larger ext3fs partition. That way, you could copy files from one partition to the other if you want to access them in Windows. That might or might not be preferable to using a separate USB flash drive.

---

### Post by ClientAlive on 2011-05-16
Ok, I exited gparted and I "safely remove" the disk (the only option available to me in the right click menu on the icon on the desktop - and the only way I know to do it). I then launched gparted again and do not see this disk listed that I might do 'anything' with it.

So what now?

---

### Post by nothingspecial on 2011-05-16
Mount it again and try unmounting it through gparted.

Let me get this absolutely right.

You have an external hard drive, with loads of stuff on it?

But you do not care if that stuff is nuked?

And you want to format it ext4?

Is this this right?

---

### Post by ClientAlive on 2011-05-16
Ok, so it occurred to me that "umount" from the command line may not be the same thing as what I did before. So I shut the thing down, unplug it from the machine, turn it back in and plug it back in. No icon appears on the desktop and nautilus does not automatically launch as it normally did.

I launch gparted and I see that this drive is listed but I happened to notice it is not listed in gparted as . . .

```
 /dev/sdb1 
```

but as . . .

```
 /dev/sdb 
```

Nevertheless I trust what I'm being told here. So I open a terminal window and here's what happened.

```

 ~$ sudo umount /dev/sdb1
[sudo] password for shine: 
umount: /dev/sdb1: not found
shine@lineNine:~$ sudo umount /dev/sdb
umount: /dev/sdb: not mounted

```

So I close the terminal window and open gparted again (I had closed it to do the "umount" in terminal). I go through the selections and execute the actions. gparted runs the job and all seems fine. It tells me the job was completed successfully.

What I don't get is how odd this seems to have played out. When I powered the disk back on and plugged it in again it did not seem to be recognized (no icon on desktop, no nautilus). When I ran the "umount" command in the terminal it gave me error messages (for lack of a better term). When I went back into gparted: not only did the disk show up in the list but the thing ran the job and did what I wanted done. What the hell?

Anyhoo... sorry I was so retarded about this. I just am not familiar with how Linux does some things. On windows I could have done this in about 10 min w/o any help. I must admit I am really just wierded out about the way it happened though.

I went with ext3. Don't want to count my chickens before they hatch. This disk still does not show up in nautilus and I don't see any way to eject it or safely remove it. I think I'll try a restart and hope for the best.

gparted showed 3.84 GB being used after the operation was complete. I wonder what is going on with that?

Well, here goes . . .

---

### Post by nothingspecial on 2011-05-16
Hi, ClientAlive,

I believe we have met before (a punk shoutcast stream?)

I don't know what you are doing wrong, and to be honest I am unfamiliar with gparted. However the principals ought to be the same.

When you plug a usb hard drive into linux, it knows it is there. Weather it is mounted or not.

Being mounted is not the same as plugging it in through a usb port.

However, due to the auto mounting software that ubuntu uses it may appear this way.

When you mount an external usb device (or cd/dvd for that matter), you are telling ubuntu where it should be in the file system.

you can mount an external device anywhere.

For example, I have 2 external drives mounted in my music folder. This is useful because my internal disc is not big enough for my music collection.

I've said before to you (I think), stop thinking windows!

This is a completely different way of doing things (no offence meant :p)

I can show you how to do it cli style, if you like, but i'd rather you did it through gparted. (again no offence meant :p)

---

### Post by nothingspecial on 2011-05-16
It seems my last reply is redundant, however

after the reboot, weather or not it appears on your desktop, it should appear in our places menu??????

---

### Post by nothingspecial on 2011-05-16
> **ClientAlive said:**
> 

```
 /dev/sdb1 
```

but as . . .

```
 /dev/sdb 
```



```

 ~$ sudo umount /dev/sdb1
[sudo] password for shine: 
umount: /dev/sdb1: not found
shine@lineNine:~$ sudo umount /dev/sdb
umount: /dev/sdb: not mounted

```



ClientAlive,

Again, I do not want to be rude, but from your posts, it is obvious you do not actually understand what you are doing..........

....... and the reason I reply to you is that I think you should, before you do this.

/dev/sdb is (sort of) your external disc.

/dev/sdb1 is a partition on your external disc.

You don't mount or unmount hard discs.  You mount and unmount partitions (file ou.systems)

Make sure you know what you are doing , before you do it.

I do not wish to offend  Y:pou

---

### Post by ClientAlive on 2011-05-16
> **nothingspecial said:**
> Hi, ClientAlive,

I believe we have met before (a punk shoutcast stream?)



Oh yeah, the was you wasn't it?! That was really cool! I loved that!

> **nothingspecial said:**
> Hi, ClientAlive,

I believe we have met before (a punk shoutcast stream?)

I don't know what you are doing wrong, and to be honest I am unfamiliar with gparted. However the principals ought to be the same.

When you plug a usb hard drive into linux, it knows it is there. Weather it is mounted or not.

Being mounted is not the same as plugging it in through a usb port.

However, due to the auto mounting software that ubuntu uses it may appear this way.

When you mount an external usb device (or cd/dvd for that matter), you are telling ubuntu where it should be in the file system.

you can mount an external device anywhere.

For example, I have 2 external drives mounted in my music folder. This is useful because my internal disc is not big enough for my music collection.

I've said before to you (I think), stop thinking windows!

This is a completely different way of doing things (no offence meant :p)

I can show you how to do it cli style, if you like, but i'd rather you did it through gparted. (again no offence meant :p)


I didn't want to do something like this cli style because I was worried about making a mistake that could really cost me. If I were to put the wrong information in or in the wrong order I could nuke my whole system.

So here's what I've found/ where I'm at:

After reboot the drive does show up both on the desktop (icon) and in places. Good so far I'm thinking . . .  So I open up the drive and I see a "lost+found" folder in there. I try to open it and it tells me I don't have permission. Ok, whatever - I think. I look at it's properties. It tells me it has 217.4 GB of free space! What! That's almost the whole drive! I close the nautilus window and I open it again (open the drive) and I select the properties of the "lost+found" folder. This time it lists the free space as "unknown". I double click the folder, am told I don't have permission (as I figured I would be) slect the drice in places again (since the "lost+found" folder shows up as a subdirectory under the drive in the places pane), and I then select properties again - this time it reports the free space again (same quantity as specified above). Now I try to drag an open office document from the desktop into the nautilus window (to copy it into the drive as a test. I get the following error message:

> 
Error opening file '/media/Lacie/gparted_details_01.odt': Permission denied


the name of the file was "gparted_details_01.odt"

So what is going on here?

Recap:

gparted lists:

Used: 3.84 GiB
Unused: 229.04 GiB
Size: 232.88 GiB

And the properties of that "lost+found" folder give:

Free space: 217.44 GB

On top of it all, the attached picture seems to say it all . . .

The only new piece of information in that picture is the 11.8 GB listed as used space.

232.88 - 217.4 - 3.84 = 11.64

Still there is something missing here. Nothing adds up!

Nevertheless, apparently it is the "lost+found" folder that is the free space. Hmmm . . .

None of it makes sense to me guys.

I don't know what to do besides trying to run it again. I won't do anything till I hear something back though.

Thanks

---

### Post by nothingspecial on 2011-05-16
> **ClientAlive said:**
> Oh yeah, the was you wasn't it?! That was really cool! I loved that!




I didn't want to do something like this cli style because I was worried about making a mistake that could really cost me. If I were to put the wrong information in or in the wrong order I could nuke my whole system.

So here's what I've found/ where I'm at:

After reboot the drive does show up both on the desktop (icon) and in places. Good so far I'm thinking . . .  So I open up the drive and I see a "lost+found" folder in there. I try to open it and it tells me I don't have permission. Ok, whatever - I think. I look at it's properties. It tells me it has 217.4 GB of free space! What! That's almost the whole drive! I close the nautilus window and I open it again (open the drive) and I select the properties of the "lost+found" folder. This time it lists the free space as "unknown". I double click the folder, am told I don't have permission (as I figured I would be) slect the drice in places again (since the "lost+found" folder shows up as a subdirectory under the drive in the places pane), and I then select properties again - this time it reports the free space again (same quantity as specified above). Now I try to drag an open office document from the desktop into the nautilus window (to copy it into the drive as a test. I get the following error message:



the name of the file was "gparted_details_01.odt"

So what is going on here?

Recap:

gparted lists:

Used: 3.84 GiB
Unused: 229.04 GiB
Size: 232.88 GiB

And the properties of that "lost+found" folder give:

Free space: 217.44 GB

None of it makes sense to me guys.

I don't know what to do besides trying to run it again. I won't do anything till I hear something back though.

Thanks

Do not worry, the lost and found folder is a feature of the ext* file systems. You can leave it or delete it.

To your actual problem of permissions.

Of course you cannot read and write to this file system. You created it (with sudo or gksudo) as root, and therefor root owns it.....


But because you have an admin account, you can rectify this

first, you need to see where it is mounted?

```
mount
```

It will probably be at /media

and will probably be /media/blah_blah_blah

so you have to do (I am imagining your user name is ClientAlive --------- if it is Joe or Bob etc change it)

```
sudo chown -R ClientAlive:ClientAlive /media/blah_blah_blah
```

Then ou should be good to go :D

---

### Post by ClientAlive on 2011-05-16
> **nothingspecial said:**
> Do not worry, the lost and found folder is a feature of the ext* file systems. You can leave it or delete it.

To your actual problem of permissions.

Of course you cannot read and write to this file system. You created it (with sudo or gksudo) as root, and therefor root owns it.....


But because you have an admin account, you can rectify this

first, you need to see where it is mounted?

```
mount
```

It will probably be at /media

and will probably be /media/blah_blah_blah

so you have to do (I am imagining your user name is ClientAlive --------- if it is Joe or Bob etc change it)

```
sudo chown -R ClientAlive:ClientAlive /media/blah_blah_blah
```

Then ou should be good to go :D


So even though it appear it is this "lost+found" folder that contains almost the entire disk worth of space - I can just delete it?? And that won't hurt me??

And what about all the crazy differences in what is shown for used and free space?

Did you see the pic I added?

Just want to make doubly sure before I do anything.

Thanks

---

### Post by nothingspecial on 2011-05-16
> **ClientAlive said:**
> So even though it appear it is this "lost+found" folder that contains almost the entire disk worth of space - I can just delete it?? And that won't hurt me??

And what about all the crazy differences in what is shown for used and free space?

Did you see the pic I added?

Just want to make doubly sure before I do anything.

Thanks

That's why I asked. 

as long as you do not care about the data on this drive, then format it.

feel free to wait for a 2nd opinion, I am 99.99999999999999999999999% sure nothing bad will happen. But it is (extremely unlikely) possible that I am wrong.:D

You are asking about formatting a hard disk, with no concern as to the data that resides on it. It is highly unlikely that that can go wrong.

---

### Post by nothingspecial on 2011-05-16
> **nothingspecial said:**
> That's why I asked. 

as long as you do not care about the data on this drive, then format it.

feel free to wait for a 2nd opinion, I am 99.99999999999999999999999% sure nothing bad will happen. But it is (extremely unlikely) possible that I am wrong.:D

You are asking about formatting a hard disk, with no concern as to the data that resides on it. It is highly unlikely that that can go wrong.

By format it , I mean use it :D

---

### Post by ClientAlive on 2011-05-16
> **nothingspecial said:**
> That's why I asked. 

as long as you do not care about the data on this drive, then format it.

feel free to wait for a 2nd opinion, I am 99.99999999999999999999999% sure nothing bad will happen. But it is (extremely unlikely) possible that I am wrong.:D

You are asking about formatting a hard disk, with no concern as to the data that resides on it. It is highly unlikely that that can go wrong.


Yes. It's ok. Even though I did have some investment into what was on there I hardly ever accessed it. After I switched to Linux and couldn't get into the drive bec of it, it sat there on the shelf for weeks and I never even thought about it except in the context of using the drive again.

So you use the word "format". I thought that's what I just did with gparted. What you said in you previous post was not "format" it was about deleting the lost+found folder and about changing ownership on the drive (in connections with permission issues) on the drive. Now that was what I was asking about in post #21 - the post you quoted.

Now also I think about it and wonder: 'isn't changing ownership something that is done on folders and files?' This makes me think about the lost+found folder - the one that was talked about deleting. You can't change ownership on a folder that doesn't exist (the lost+found). But this is Linux. Maybe when it mounts the drive it mounts it as a folder. In that case the "chmod" thing would make sense that it could be applied to a drive.

I could care less about the data on this drive - but - if something happens to the drive itself and I ruin it: I'll bee **** out of luck. It's all I've got and I don't have money for 'stuff' right now.

I do sure appreciate your help nothingspecial, I do, but can you please elaborate a little? This is one of those things I can't afford to have go sideways on me (get screwed up).

Thanks man.

---

### Post by ClientAlive on 2011-05-16
Yes, sorry was typing when you wrote that last thing  :D

Please don't take this the wrong way (I don't mean it anyhow weird) but I would just like to get this over with. I'm just want to be sure nothing happens to the drive itself because I mistake something you said or were talking about.

---

### Post by ClientAlive on 2011-05-16
> **ClientAlive said:**
> Yes, sorry was typing when you wrote that last thing  :D

Please don't take this the wrong way (I don't mean it anyhow weird) but I would just like to get this over with. I'm just want to be sure nothing happens to the drive itself because I mistake something you said or were talking about.



Have an appointment. Gotta go for now. Be back on 1.5 hrs.

Thx

---

### Post by srs5694 on 2011-05-16
The partition on your external drive now has an ext3 filesystem on it. That filesystem has ~229 GiB of free space available for use. Since the lost+found directory is *part of* that filesystem, you can store up to ~229 GiB of files in that directory; hence the report on that much free space being available "in" that directory.

The 3.8 GiB of used space can come from a variety of sources, including confusion over units (GB vs. GiB, etc.), miscellaneous overhead for the filesystem, and 5% of the space that's reserved for use by root. This last is the only one you can do anything about (other than educate yourself): You can use the tune2fs utility to change the reserved-space percentage, as in "sudo tune2fs -m 0 /dev/sdb1". Do this only when the filesystem is unmounted, though.

I don't recommend deleting lost+found. AFAIK, nothing bad will happen if you do, but it *is* a standard part of the filesystem. (It's used in case disk errors turn up in the future; the filesystem check utilities then dump any files they recover but can't identify in that directory.) Just ignore the directory.

In Linux, filesystems are mounted in directories -- that is, when the filesystem is mounted, it *becomes* that directory. Thus, changing the permissions on the directory at which a filesystem is mounted changes your ability to access that filesystem.

If you just issue the chown command that nothingspecial suggests, you'll be fully able to use the drive. (Note that you referred to chmod, which is different -- chown *ch*anges *own*ership whereas chmod *ch*anges *mod*es [that is, permissions]. In fact, either can be used in your case, but they'd be used in different ways and have subtly different effects.)

There's no command you can type (or GUI options you can click) that will physically destroy your drive, especially not quickly. (*Maybe* you could set up a data-access pattern that would wear out the drive's heads by overexerting them, but that would probably take weeks, if not months or years, to do any harm.) The biggest risks to an external drive are in the form of physical trauma -- being dropped, being zapped with a static discharge, etc. You *can* destroy your data with a command, but even that sort of error can usually be corrected if you know how. (I don't recommend you test the last part of this statement, though!)

---

### Post by ClientAlive on 2011-05-16
> **nothingspecial said:**
> Do not worry, the lost and found folder is a feature of the ext* file systems. You can leave it or delete it.

To your actual problem of permissions.

Of course you cannot read and write to this file system. You created it (with sudo or gksudo) as root, and therefor root owns it.....


But because you have an admin account, you can rectify this

first, you need to see where it is mounted?

```
mount
```

It will probably be at /media

and will probably be /media/blah_blah_blah

so you have to do (I am imagining your user name is ClientAlive --------- if it is Joe or Bob etc change it)

```
sudo chown -R ClientAlive:ClientAlive /media/blah_blah_blah
```

Then ou should be good to go :D


Ok, so, I got to re-reading something you said in you last post in this thread and it kinda sunk in I guess. You said:

> **nothingspecial said:**
> You are asking about formatting a hard disk, with no concern as to the data that resides on it. It is highly unlikely that that can go wrong.

I guess you're right so I went for it. Used "chown -R" as you instructed and then went in and deleted the folder. Drive seems to work fine. I can copy files into it and delete them. Ok - but now there's this other odd issue. I can't make sense of certain space (and I mean it's big enough to think it's not just a difference in how one program or another calculates it).

Thanks for your help nothingspecial and srs5694.

I see what you are saying srs5694. That's cool w/ me if the consensus is that things are normal and there isn't anything funny going on. Kinda too late on the lost+found thing. I'm sorry man. It's just that I'm approaching the 24 hr mark on this deal that shouldn't have taken but about 5 min. I got sick of dealing with it. I sure appreciate the way you explain things to me though.

If you tell me that what is pictured in the two attachments is normal I'll believe you man.

I wonder now if not having that lost+found folder in there might make it so I lose the restore functionality I might have had? I sure as heck wouldn't have wanted to have that lost+found folder just floating around amongst all the other stuff as I start to fill the drive. You'd think they could have at least made it a hidden folder. I know that adding a dot in front of the name makes it hidden but then maybe changing the name screws something up. Guess it doesn't matter now.

But if you think what's in the pictures is normal I'll listen and just kick back and enjoy my fresh drive.

Thanks man.

---

### Post by srs5694 on 2011-05-16
I wouldn't worry about it. I don't use the GUI tools very much for such things, so I can't say what GParted vs. Nautilus (or whatever produced the pie chart) is reporting. Given the three factors I listed, though, there can be a lot of variability between programs depending on what each does.

As to deleting lost+found, it's *probably* OK; the reason I advised against it is precisely your concern, but that's a concern based on ignorance -- I don't happen to know what the recovery tools do if lost+found is absent. If you're concerned about it, you can unmount the filesystem, create a new filesystem with GParted or mkfs or whatever you like, mount the new filesystem, and then change the permissions. The result will be a fresh start, complete with a new lost+found directory. This will take just a few seconds, and with no data on the disk, it might be worth doing.

---

### Post by ClientAlive on 2011-05-16
..............................

---

### Post by ClientAlive on 2011-05-16
> **srs5694 said:**
> 
In Linux, filesystems are mounted in directories -- that is, when the filesystem is mounted, it *becomes* that directory. Thus, changing the permissions on the directory at which a filesystem is mounted changes your ability to access that filesystem.



This thing (Linux) is just odd. I guess it's gonna take some real getting used to. I remember when I first started fooling around with the command line. It made me really uncomfortable. I know now that it's just as, if not more, reliable. Just that I wasn't used to not being able to see the little folder icons and whatnot. I'm laughing about this now but I sure didn't think it was funny in the beginning.  :)

> 
If you just issue the chown command that nothingspecial suggests, you'll be fully able to use the drive. (Note that you referred to chmod, which is different -- chown *ch*anges *own*ership whereas chmod *ch*anges *mod*es [that is, permissions]. In fact, either can be used in your case, but they'd be used in different ways and have subtly different effects.)


I should know better. Lord knows I"ve been doing enough studying. [chown uses username:groupname and chmod uses a four digit hex number or symbolic notation]. Just that when it comes to applying that reading one has been doing it's a little different. When it's something real and something you care about you start to wonder whether you understood stuff right. I think I just made a type-o. I know better what the difference is.  :P


> **srs5694 said:**
> 
There's no command you can type (or GUI options you can click) that will physically destroy your drive, especially not quickly. (*Maybe* you could set up a data-access pattern that would wear out the drive's heads by overexerting them, but that would probably take weeks, if not months or years, to do any harm.) The biggest risks to an external drive are in the form of physical trauma -- being dropped, being zapped with a static discharge, etc. You *can* destroy your data with a command, but even that sort of error can usually be corrected if you know how. (I don't recommend you test the last part of this statement, though!)



I don't know why (well, actally I do but I'll get to that) I had this crackpot notion that the drive might contain some piece of software that it needs to be recognized when you plug it in. Funny thing is, I used to own a drive (a different one) that had some software installed on it. An external drive with that. Now that I recall though, it was possible to remove/ erase that software and not hurt anything. It was just some extra the manufacturer put on there.

Thanks for all your help. Both of you. I'd have really been stuck without you guys. Instead of a one day project it could have easily become a one week project or more (trying to figure it out on my own). Then who knows if I make the choices that lead to the best/ optimum outcome.

**nothingspecial** there's something I need to say. Never once did I think that you didn't know what you're talking about. That would just be absurd for me to even think. It's just that, like I touched on above, when you have something that you care about, and you aren't sure about anything at all with something you're about to do to it, you start to think crazy thoughts. Thoughts like, 'well maybe he missed something, I wonder if he saw (such and such), or what if I did this and that happened?' Fact of the matter is this stuff is as simple as breathing to you, I'm sure. I'm the one that worries.

I sure appreciate you man.

Have a great week.

:D

---

### Post by nothingspecial on 2011-05-17
> **ClientAlive said:**
> 


**nothingspecial** there's something I need to say. Never once did I think that you didn't know what you're talking about. That would just be absurd for me to even think. It's just that, like I touched on above, when you have something that you care about, and you aren't sure about anything at all with something you're about to do to it, you start to think crazy thoughts. Thoughts like, 'well maybe he missed something, I wonder if he saw (such and such), or what if I did this and that happened?' Fact of the matter is this stuff is as simple as breathing to you, I'm sure. I'm the one that worries.

I sure appreciate you man.

Have a great week.

:D

No problem.

Infact you are absolutely right to be 100% sure you understand what a command (or anything that requires your password) is going to do. That's kind of what my sig is trying to say.

If you tell linux to do something, then it does it, doesn't ask you if your sure :P it just does it.

But remember, so long as you have all your important data backed up, nothing can go horribly wrong.

---

### Post by nothingspecial on 2011-05-17
Once you get your head round mounting it's a very useful concept.

All you are doing is positioning a partition somewhere in your file system.

I'll give you an example. My computer has over 500 gigs of music in my Music folder. But in reality it doesn't have any music at all.

It all lives under the stairs on my server (nothing fancy, just an old pc).

But the server's harddrive is less than 500 gigs.

The servers home directory is a seprate partition. It is mounted at /home.

In /home/ns/music there are 8 folders


```
ls music
audio-books     Compilations  Grateful Dead  radio
BBC_Proms_2010  flac          mp3            rips
```

but only 6 of them are on the servers internal hard drive. flac and mp3 are on 2 different external hard drives.

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  3.6G  7.5G  33% /
/dev/sda3             126G   64G   55G  54% /home
/dev/sdb1             459G  383G   53G  88% /home/ns/music/flac
/dev/sdc1              74G   61G  8.8G  88% /home/ns/music/mp3
```

So my music folder is spread across 3 physically different hard drives but it's all in one folder.

Then this folder is remotely mounted to my computers (in a different room) /home/ns/Music folder remotely. Like this

```
:~$ ls Music/
:~$ sshfs -o idmap=user ns@192.168.1.11:/home/ns/music/ /home/ns/Music
:~$ ls Music/
audio-books     Compilations  Grateful Dead  radio
BBC_Proms_2010  flac          mp3            rips
```

At first, before I mount it there's nothing there. But after I use sshfs to mount it remotely it's all there and available in my Music folder. But none of it is actually there. The contents of my music folder on my pc is actually a combination of stuff spread across 3 different hard drives in another room........

...... but it's all in one folder - and rhythmbox/banshee etc etc don't care.

I hope that makes sense. :D

---

