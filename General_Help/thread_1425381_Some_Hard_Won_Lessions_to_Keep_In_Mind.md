---
title: "Some Hard Won Lessions to Keep In Mind"
date: 2010-03-09
forum: General Help
---

### Post by oldefoxx on 2010-03-09
My wife wanted to know how I could just sit, day after day, at a computer and seem satisfied.  Easy.  Computers have been my career focus since about '65 and though I don't get paid for it now, there is still much to do and learn.  And there is a lot of learning to do.

There was a really long thread here, which discussed (or argued) the point of why stay with Ubuntu when it is easy enough to go back to Windows XP.  I think the same arguments were repeatedly employed in the 4,000 plus posts, but always in yet another person's words.  You got away from the topic for awhile, you might as well jump right to the last page because it was almost like starting over.

Now my Windows choices are limited.  If possible, I go with Windows 2000.  If necessary, I go with Windows XP next.  I won't repeat the arguments for or against either here.  But I am not going to move on to any later version of Windows, and I see no reason to ever do so.

I helped my sister-in-law get a refurbished HP Pavilion P6112P desktop at a good price, but I told her that I was not going to get involved in supporting Vesta or Windows7.  There was not enough justification for doing so, so if she wanted my support, it would have to be Windows under Ubuntu and VirtualBox.  She agreed, as had my wife, though my wife is not entirely sold on the whole idea.

Putting Ubuntu, VirtualBox, and Windows on the new PC was easy enough, but I have to convert programs and settings from one partition to another to squeeze it all together.  This is not easy, and I am working on code to deal with some of the issues.  There appears to be nothing available for what I am attempting, but there have been a number of requests for a tool to make it happen. I think I know enough to bring it together.

To do what I want, I have to install Windows 2000 to a partition and work from there.  But it would not install.  Searching for answers to why I got a BSOD about an inaccessible_boot_device, I learned that it could be a problem with a USB attached CD-ROM drive.  That was not the case here.

Days later I had read enough articles and postings to recognize that it could be something else entirely:  The use of SATA1 controllers in the PC that kept the installer from recognizing the existing hard drives.  Turning to Setup, I tried each of the three settings allowed:  IDE, RAID, and AHCI.  The default setting was RAID.  I tried to install Windows 2000 using all three settings, but the only install that worked was Windows XP with the IDE setting.  That was a start at least.  But as warned by one site, using IDE really slows drive operations down.

I kept looking and there are chipset drivers for the Intel G33 chipset, but mostly for XP.  However, Windows 2000 and XP are akin enough that these will often work.  I found several sources, including Intel, and pulled down about a dozen sets for graphic, chipset, audio, and so on.  I pulled these together in one folder, keeping the most recent of each file type, then burned the contents to a CD,  I also used nlite to burn an image of the Windows 2000 installer with USP5.1 incorporated.  With this, I was able to finally get Windows 2000 to recognize the SATA drives when the setting was placed in the IDE position.  The drivers disk was then used to get a high resolution video driver in, have the ethernet controller recognized, and add sound.  But it still cannot work with the PC if the SATA1 controller is in either of the other two positions.

And we are already past SATA1.  That should tell you something right there, which is, it is going to be virtually impossible to get older versions of Windows to install on and work with the hardware that is coming down the pike.  You can love Windows XP to death, but what happens when you decide to go with a new PC or replacement motherboard?

To me, this makes a new reality where the best course of action is to adopt something like Ubuntu, mix in something with it like VirtualBox, and be glad that you can continue to provide a nest for your favorite version of Windows, if that is what you want to do.

Sort of puts the whole topic of whether to go back to XP or stay with Ubuntu rather irrelevant in my mind,  Just some fresh insights based on the recent failures and successes that I've had to deal with

---

### Post by oldefoxx on 2010-03-09
Before I headed off to bed, I made the decision to try and load my sister-in-law's True Image backup onto my own HP Pavilion A6600F desktop, giving up my contents for a time just to resolve her problems.  For just two partitions with FAT32 of less than 30 GB each, it took about 10 hours to restore.  That was with version 11.  Not sure how later versions would have faired.

Bad thing about True Image is that if you make a backup with one version, you can expect that earlier versions cannot read it (file formats do change), but that later versions cannot restore earlier versions?  Now that is bad.  That means I have to keep on hand Restore disks for every version of True Image and try each in turn until one recognizes the internal structure of the .TIB file type made by a previous backup.  I even found that version 11 appears to have at least two .TIB formats in use at different times, and you have to have the right Restore disk for whichever one is needed.

Another limitation of True Image is that while it can backup and restore partitions with different file structures, and runs on some verson of Linux when using the Restore disk, it really only seems to work with FAT and NTFS contents - backing up the other partitions is more likely to be a sector-by-sector method, which makes those partition images really bulky and takes more time.  Another disadvantage is that restores have to be pretty much to the same file structure type, though it will let you choose between FAT16 and FAT32 for FAT, but you cannot move from FAT to NTFS.

But hey, version 11 dates back a ways, and if there were more information about what can or cannot be done with newer versions, I might be tempted to upgrade.

I was real disappointed to find that I could not get the Recovery disk to load and run as it should when in the client mode under VirtualBox.  That means I cannot take an existing image and bring it right into a VDI and deal with it from there.  Apparently it could not see the virtual hard drive at all.  I tried installing Windows 2000 first, then using True Image again, but it just would not go.  I noted that VirtualBox has added as second drive support feature, but I guess I will have to read the instructions, as I could not figure out where it was - it did not show up as a drive letter or anything.  

Seems I am talking about non-Ubuntu matters I suppose, but really this is just part of a campaign to bring it all together and move on with it.  A backup tool that is not restricted to certain file systems is needed, and if it works under a VM, that is even better.  But it has to be able to read and work with existing backups, otherwise what you have from the past is at risk of being lost.  Since we are pretty much past the days of the floppy drive, we are not restricted on space so much, so our CD or DVD with our backup software can have a variety of modules to call upon in order to get what's needed done.

You know what is needed?  A software toolbox, one that has everything in it for the person that has all sorts of matters to resolve.  You see real toolboxes for sale out there, with a smattering of handtools to get started with, but hardly ever a toolbox you would consider complete just as it comes.  So you have to be able to add more tools as you find them.  And you have to have some idea of what should be in that toolbox or available to add to it.  Here are some of the thoughts that come to mind:

To add a SCSI or other driver to a Windows 2000 install, you have to press F6 and stick a disk in drive A.  So some disks or drivers to add new features to Windows, and a means to make them appear as though on drive A (the floppy you are less likely to have as time goes on).

Most basic features for PCs are presented as integrated into the motherboard, and that means sets of drivers are required for the different motherboards and operating systems being put together.  Some place where you can locate and download a set of drivers that will work for you.

Backup and Restore software that not only fills a gap with multiple OSes and hardware platforms out there, but can process and recover the contents of older backups, even read from tape drives if that is where the backup is stored.  They can also present the contents of backups as though having direct access to the partitions, folders, and files contained therein (this is a nice feature of True Image, and sometimes helps a lot).

An external hsrd drive or two. Not software per se, but a good place to store software or just the occasional backup or two.  I'm sure others have ideas along these lines as well.  Don't forget LiveCDs.  How would we ever get by without them now?

---

### Post by cpressland on 2010-03-09
Wow, you've taken the longest route in history around doing all this, not to mention running a Virtual Machine as the primary use on a Machine? Yeah because having essentially no hardware acceleration is always fun. Seriously, Windows Vista and Windows 7 are more than mature enough now and are leaps and bounds better than Windows 2000 and XP. I'd have just installed Windows 7 on the box, all drivers would have worked by default, then used bog standard software to restore all the documents and settings.

I honestly cannot understand why you've taken such a long route around all this? Pride? Linux is good and all, but if somebody wants XP or Windows 7, just darn well install it native.

---

### Post by oldefoxx on 2010-03-12
> **cpressland said:**
> Wow, you've taken the longest route in history around doing all this, not to mention running a Virtual Machine as the primary use on a Machine? Yeah because having essentially no hardware acceleration is always fun. Seriously, Windows Vista and Windows 7 are more than mature enough now and are leaps and bounds better than Windows 2000 and XP. I'd have just installed Windows 7 on the box, all drivers would have worked by default, then used bog standard software to restore all the documents and settings.

I honestly cannot understand why you've taken such a long route around all this? Pride? Linux is good and all, but if somebody wants XP or Windows 7, just darn well install it native.

Ah, but when Vista or Windows7 finally crashes, or you change enough of the hardware to invalidate them, won't it be such fun to find that you can't get it back, and will likely have to reinstall it from a new purchase or work out some settlement with Microsoft's technical and customer support?

And let us not forget the pleasure of buying new editions of much of your working software just to migrate from what you had to what you now have instead, or do without.  I've heard said that Windows7 provides a mode for running existing applications as though under a prior release of Windows, but they did the same thing with XP, and it was hardly used.  Might have been because it was a bit hard to use.  And with XP, it did not always suffice.

And perhaps you missed my point, when you say "... but if somebody wants XP or Windows 7..." that certainly does not include me.  If I somehow conveyed a different impression, sorry about that.

Now were I to adopt Vista or Windows7, I might come to appreciate it, but I do not like the way this game is being played, and feel I would just be giving in to the other faction at my expense.  And there has already been too much of that going on.

See, the problem with Windows 2000 and XP is not that they are bad in and of themselves, but they belong to the camp that exploits its followers by requiring that you periodically replace them with something new, and in some ways (hopefully appealing), different.  Windows 2000 and XP can't cope with the new hardware out there because they are not maintained.  The only real fixes are aimed at security flaws, but that is just to protect the reputation of Windows in general.

Linux, on the other hand, is constantly under review and revision, and some flavors of it do quite well in the presence of new hardware.  I am just looking at the latter as a means of preserving and continuing to use some of the former.  Without VM options, this would be largely impossible, or hugely impractical.  But with decent VM software available, that is no longer the case.

Acronis' True Image software, at least with version 11, has a problem with recognizing a virtual hard drive as provided by VirtualBox, at least up to the point where the virtual hard drive is flagged by type and formatted.  To do that, you may have to resort to using DOS, Windows, or possibly even Linux as the client, and do an initial install.  After that install, True Image can now recognize and do what it needs to do to restore a partition or a group of folders and files, as you choose.

I set aside enough virtual hard drive space to encompass the three partitions of my sister-in-law's old PC, installed Windows 2000 there, then used a Recovery disk of True Image, and elected to restore all three partition over the one that Windows had set up.  My first effort at doing something like this.  One partition would have been fine, but three?  What will that do?

Well, first it made it very slow.  My restore is taking about ten times longer than normal.  After hours of seeing the FAT32 image of drive C: being restored over local C:, and 16 kb clusters changed to 32 kbit clusters, I figured maybe all that extra time was justified.  I mean you are changing from NTFS to FAT32, changing cluster sizes, and the whole virtual drive was only dyamically allocated in the first place, and you also have to update the FAT table as you progress.  Assuming that the intent is to retain a consecutive sectored virtual drive, there may even be a lot of file rearrangement and redistribution taking place at Ubuntu's level.

Had a long night's sleep, with the promise of 1 day and 8 hours of restore to go through, and got back to the PC today to see 23 hours remaining.  But the restore of drive C: seems complete, because I now see drive D: being restored to F:, and almost half through.  Where is this drive F?  Is it right behind C, where I would think it should be, in which case the old E drive should restore behind it as either drive E or G.  I can understand the skip from drive D, because that is assigned to the CD-ROM drive by VirtualBox, but it is not yet clear to me why the letter E was skipped, unless True Image made note that drive E was to be restored to its original partition.  See, I hope to learn something from all this.

That is not to say that everything is perfect with the Ubuntu+VirtualBox arrangement when setting up Windows 2000 as a client.  It installed okay, but crashed with a BSOD on reboot.  The same with each reboot.  The message displayed reports that **kmode_exception_not_handled**, which on research, tells me very little.  It will boot in the safe mode though.  Best that I can determine at this point is that it somehow is driver related, or device related.  Don't you love how informative such messages can be?

Obviously many people wonder "Why bother writing something out if you do not know yet if you will be successful?".  Others ask, "Why don't you just keep a journal?".  I find that postings like this work best for me, because I have to explain everything well enough for others to follow, and it brings some clarity of thought to the process.  it may also help others to some extent, even if just to see how you go through a process like this.  And it may help me, if someone out there has something related that could be of help.

---

### Post by Steven_S on 2010-03-13
> **oldefoxx said:**
> ... but it is not yet clear to me why the letter E was skipped, unless True Image made note that drive E was to be restored to its original partition.

This whole post is way above my head, but this little element I can say something about: The E-drive is usually automatically assigned to usb sticks and SD cards. At least, that is what I gather from my experience with default XP.

Good luck with your efforts! I would say that, unless your sis-in.law really uses Windows-only software, I would get her to try the normal Ubuntu on that machine (you can even make it look like Windows) ;)

---

### Post by indytim on 2010-03-13
> The E-drive is usually automatically assigned to usb sticks and SD cards. At least, that is what I gather from my experience with default XP.


It's dependent upon how many opticals the box has.  If one optical, then "E".  If 2 opticals then "F".

IndyTim

---

### Post by snowpine on 2010-03-13
You may do whatever you like on your personal computer of course :) but the bizarre solution you're promoting to your friends and family is just plain irresponsible, IMHO. All operating systems have a fixed period of support ("end of life") and Windows 2000 reached its sell-by date in 2005. Frankly, they should not even be supporting XP any more in my opinion.

Lest you think I am biased against Microsoft, I would not recommend an obsolete version of Ubuntu (pre-8.04) either. Using an unsupported operating system is simply put a security, stability, and compatibility nightmare.

If they want to use Ubuntu as their everyday operating system, and you want to support it, I think that's great (yay Ubuntu!) but as a virtualization platform for an unsupported Microsoft release it makes no sense. Your wife is right to be skeptical; if it were me, I would let her use whatever operating system she wants rather than strain the relationship.

All in my opinion, of course. :)

---

### Post by oldefoxx on 2010-03-14
Hmmm.  My response to the last post was wiped.  Too bad.  It was not inflammatory and it had some good points about what my efforts have now shown me.  Let's move right on to those points, as they might benefit others.

My effort to install three small partitons over one large one were successful, and the assigned drive letters were C:, D: and E:.  The result was that the CD-ROM drive was bumped to F:.  That makes it unnecessary to work around Windows' method of using drive letters when setting up a client under VirtualBox.  So that is real good.

Checking the set up volumns was good, but I ran into a glitch with VirtualBox, so wrote a bug report and sent off the log as requested.  Might lead to a fix later on.  Not an impairment with what I am doing now.

None of the restored Windows partitions would boot.  Trying to repair them from the install disk was mostly unsuccessful.  Worked out what the problem is though.  When you restore Windows from a backup, it contains drivers to devices on the old pc.  If those same devices are not found on the new PC, expect that the effort to boot Windows will fail.  A Safe Boot mode may skip some of these lacking devices and drivers.  But just trying to repair or recover is not adequate, since existing drivers will be left in place.

What is needed is a way to force the installed version of Windows to relinquish its hold on those drivers and go through a new detection process for devices and available drivers during the install.  The new detection effort is automatic, but not the step of getting rid of any existing drivers first.  I've never heard of this approach being used before, and have not had time to research it further yet.  Overall though, this is a remarkable gain for any that contemplate moving to Linux+VirtualBox+existing Windows as clients, or in the case of Ubuntu, Ubuntu+VirtualBox+existing Windows, and the existing Windows can be from backups.

You know what you might be seeing here?  a regain or reestablishment of faded PC memories, because if you still have backups, you can get much of it back in virtual space, and then save and reuse all that in a set of VDIs, and not have to give up your machine of the present or future in order to make use of much of this.  Could be quite interesting.  Might even make it so that you can chug some of those setups around with you, or make it so that one PC can serve the needs and interest of several, but at different times of course.

Of course VDIs tend to be rather large in size, but now this might serve to give you good reason to buy into the whole concept of blue ray burners.  Either that, or reliance on external hard drives.

Hmmm, to the point of forcing others to accept Ubuntu+VirtualBox+Windows as conditions of my continuing efforts to help them, I am just coming to terms with where my interests are and how much time and effort I am willing to devote to their aid when it goes beyond what I can accept for myself.  I don't get paid for what I do, and this is the only payback I ask, is that they concent to doing it my way.  If not, they are free to search elsewhere for assistance.  That makes it simply their choice in this matter, and that is as fine as I can make it.

---

### Post by seenthelite on 2010-03-14
I have XP in Virtual Box in Ubuntu 9.10 and it took about 20 minutes just put the XP disk in the drive and installed.

---

### Post by RabbitWho on 2010-03-14
All you had to do was dual boot, you created the problems for yourself. 

If windows did eventually crash as you feel sure it would, they could still access all the stuff through the linux partition. 

I think you just wanted to role up your sleeves, come in and say "Stand back! Stand back! I'll do it! I know about computers! Windows!? No no no! You don't know what you're talking about! LINUX!" 
It's like a mechanic insisting on putting a Ferrari engine in a car when the person only wants to drive to the shop and work and back.

---

### Post by oldefoxx on 2010-03-14
My reasons and motivations are not necessary to this discussion.  However, if you want to assume the worse and put your own name to them, I am not in a position to stop you.  It puts me in mind of the saying that those those that can, do.  Those that can't just criticize.  Or is it teach?  I guess it depends on what community you are part of.

Way back when, I deemed that there had to be a way to go other than stick with Windows.  Linux seem to be the most promising and least expensive alternative, but at that time, it was mostly command line oriented.  That would not suit many people.

Ubuntu and VirtualBox together make all the difference.  The combination is very solid and getting better.  VirtualBox is not needed unless you want to add something like Windows to the equation.  Dual boot sugestions are not even considered for two significant reasons:

(1) To go from one to the other means a complete reboot.  That does not work well if frequent trips from one to the other are involved.

(2)  The added advantage of having a complete surround of Windows for protection with Ubuntu and VirtualBox providing the safeguards would be lost.  That means layering Windows will all sorts of programs for keeping malware at bay, but with limited success.  I read that soem 20 million new viruses were released against PCs this last year, more than all the years previously combined.

It's not that Ubuntu or VirtualBox is absolutely impervious, but you are making the whole situation a whole lot more complicated, and with many people involved with both, you can be more assured that hackers will look at the huge pool of relatively unprotected targets out there first.

I don't care if you as a home owner and uwer of a PC care about the idea of Ubuntu and VirtualBox in combo together, but suppose I were a business owner or IT professional and faced with what a company with older PCs and versions of Windows losing support from Microsoft:  Should they pay out big bucks for upgrades, or keep waiting awhile?  This whole approach adds a third option, which is do neither but go with a mix where they can run their older software on newer hardware by sticking it inside a new merge of two products, and their outdated software will receive better protection than before.  To me, that approach is a no-brainer as to which way to go.

Now the way I left it, I was getting crashes after doing a repair of a Windows install.  The most apparent symbol was a BSOD, and the messages on it had little to really say.  But you go through enough of them, you pick up a pattern.

First, Safe Mode might show you Mup.sys as the last module to be loaded, then the crash occurs.  Sorry, Mup.sys is the last module to laod properly, the failing module is the one right after.  What module is that?  It is called fltmgr.sys, and stands for file filter manager.  What is its problem?  Well, Microsoft has put out over a hundred patches and upgrades for Windows 2000, and what is tripping up fltmgr.sys is that there is a hook requested in ntoskrnl.exe, but the access point does not exist, so rather than keep going, fltmgr.sys puts a break on everything.

This is a case where the old does not match up correctly against the new.  Using an original install disk for Windows 2000 Pro, you are trying to reinstitute the old.  But soemthng out there is looking for something newer.  Turns out that there was a feature added in one of the updates that happend with Rollup 1, a collection of upgrades that came out after SP4 was released.  You cannot have a normal boot process complete until you rectify this problem.

How to do that?  Use the F8 key and go into Safe Mode for each boot effort during the install process.  This acts to prevent this error from occurring.  What you would like to do then is go through the Windows update process, but you probably can't.  Windows will likely just seem to lock up.  Instead of using Windows Update, just execute the USP51 or USP5.1 file found online.  It encompasses all the updates for Windows 2000 well past SP4, and finally your Windows repair efforts will have completed.  And don't forget to run the GuestAdditions that come with VirtualBox.

Man, this was a tough one.  You can check the Device Manager under Control Panel/System, but likely everything will look fine.  Remember that Safe Mode prevented some drivers from loading, and without drivers,
some devices may not even show up. My first guess would be that a lot of devices and drivers might get mapped in the Registry, but if drivers go by the same name, just soem with different dates and sizes, how can you tell what is suppse to be there?
  

Like I said, it was never a question of installing Windows as a guest under VirtualBox.  That is pretty straight forward and usually goes quite well.  This was just my first effort to devise a way to work from backups.  Don't know why none of the backups booted on first try afte the restore, but at least it looks like something you can work around.

---

### Post by oldefoxx on 2010-03-15
One thing that Windows does that is particularly hard to get back the way it should be is the manner in which letters are assigned to drives.  Your BIOS might have one method, your Windows installer another, and a tool like Acronis' True Image yet another.  And Windows caps this yet again by considering primary partitions first, then logical ones, and if something happens to cause one of the partitions to drop off the map for just a bit, the letter order can get switched around, which is bad because specific letters appear in many of the path statements in the Registry, and in links (also called shortcuts).  Best think to do is set the drive letters back the way that they were originally,
but while Windows cooperates to some extent, it will not let you change whatever it sees as having the one with the system on it.

A similar but less severe problem happens with Ubuntu, because you can delete, create, resize, and move partitions, and designations like /dev/sda1 may be changed to /dev/sda7.  There is no good way to change these back either.  This is probably a principle reason for references to partitions under Linux to use the embedded UUID codes that formatting them adds automatically.  UUIDs offer the disadvantage that if the referenced partition is reformatted, the UUID associated with it gets changed as well.

A mess up on my part yesterday caused the D: partition to drop out of the loop, and the E: partition dropped down to become D: instead.  That made E: no longer bootable, because entries in its Registry and its links would not be in error.  Reloading the D: partitions contents from a backup, it now becomes the E: partition instead.  Now it is a task to try and get these two drives to swap letters, but Windows will not permit that if either is currently the system partition.

I can boot up in C: and try to swap them back, but this only effects the way that C: sees the other two.  Each of them would see it differently, and since you cannot work directly on the Registry of a partition that is not currently running as system (Regedit is limited in this way), you are at risk of a major screw-up if you try to go right to the files underlying the Registry of a different partition and change things there.

So what I had to do instead was wipe out all three partitions, restructure the large partition to be overwritten again, go through a full reformat of that large partition, and use Acronis' True Image to begin another full restore, which will finish sometime late tomorrow.  Then if any does not boot again, I will have to go through another repair process, use the Safe Mode technique to get it up, and when I get a chance, run USP51.exe and see if that gets me where the restore can complete.

Marvelous.  Maybe you can understand why I've really lost patience with the games that has gone on around Windows for so long, and why I just decided at last that if there was an  alternative way, I was going to find it.  This time when I get those three partitions back, the first thing I am going to do is copy the created VDI to a backup on a just-in-case basis.

The only good thing about Windows is some of the applications that run on it, and how some people don't want to let go of that investment of good money, good time and effort, and losing their access to such.

So to address that concern, I decided that the most reasonable course in going forward was to make allowances for this interest by inclusion of a means for existing versions of Windows and applications to go along as well, if you want them to.  As far as I can tell, this is the most reasonable compromise available, and you have to admit that it comes at a good price.

Oh, by the way, when trying to repair Windows from the install CD,
don't take the first R choice.  That takes you to the area where you have to put a recovery floppy in drive A:, which you probably don't have, or get use of the Recovery Console, which I can't find any good use for.  Go with Enter, then use the later R choice that comes up when you pick a partition that has an installed version of Windows on it.  That's the one that works best.

---

### Post by chillicampari on 2010-03-15
Edit- I reread the thread and still not really sure what the OP is trying to do, so nvm.

---

### Post by oldefoxx on 2010-03-17
Well, whatever it was I was trying to do, it is done now.  Let me put it this way in a brief summation:

There is a problem.  How to solve it.
Looks like Ubuntu and VirtualBox together provide the means to solve it.
Efforts show that when installing a guest OS, it all fits together.
But if working from a backup, there are more problems to solve.
Address those problems and try different means to resolve them.
Finally have the means identified for dealing with the separate problems.
Matter now identfied as being solvable if you proceed with due care and follow the right sequence of steps.
So what else is new?  Solve any problems lately?

---

### Post by chillicampari on 2010-03-17
> **oldefoxx said:**
> Well, whatever it was I was trying to do, it is done now.  Let me put it this way in a brief summation:

There is a problem.  How to solve it.
Looks like Ubuntu and VirtualBox together provide the means to solve it.
Efforts show that when installing a guest OS, it all fits together.
But if working from a backup, there are more problems to solve.
Address those problems and try different means to resolve them.
Finally have the means identified for dealing with the separate problems.
Matter now identfied as being solvable if you proceed with due care and follow the right sequence of steps.



Glad it all worked out!

> 
So what else is new?  Solve any problems lately?

Yep, sure have!

---

### Post by soltanis on 2010-03-17
I would've dual booted here. But on occasion I have run virtualized OS's as my primary OS, the one time being because I was trying to run a server for a particularly finicky software package that liked to break everything if not exactly configured right, and also only worked on one version of Linux (with one version of libraries to boot).

I then saved a drive image so I could restore it.

In any case, we stopped using that program because it sucked; we switched to an alternative.

---

### Post by oldefoxx on 2010-03-22
Putting the pieces together can be both involved and awkward.  This is often because we are working with processes that were not precisely tailored for the task at hand.  This can happen in a pure Linux or Windows environment, but as you can expect, are much more prevalent when trying to bring Linux and Windows together in some manner.  Acronis's True Image is pretty good for backups and restores, with the added benefit that it works with external drives (later versions) and even lets you mount and use a backup as though a drive itself.  Quite handy at times.

Weak spots are that backup image formats have changed, and new versions of Thue Image do not recover backups made by old ones.  You cannot just look at an image and tell which version made it either, so you may have to try several versions before one recognizes the format properly.  And in a guest environment under VirtualBox, True Image will load up, but does not recognize USB devices or shared folders.  Sort of limits your access to where you need to store that backup or recover it from.  I'm sure that these problems could be worked past, but only if there is a real market demand associated with it.  The Recovery Disk for True Image is based on Linux, meaning that I imagine someone could bolster its abilities in these areas.

Something else that comes into play here is that VirtualBox, at least the current version, shows an ability to extend the size of the new virtual drive, then run gparted as the guest and partition that virtual drive as several partitions.  These get consecutive drive letters, and the drive letter for the CD-ROM drive is pushed out accordingly.  I like that about VirtualBox.  Oh, and I refer to it as the CD-ROM drive, but it can be treated as a CD-RW or DVD drive as warranted.

What I cannot buy is a dual-boot or multi-boot approach as a well considered solution.  There was a time when it was necessary, and I did my share of setting up such machines, but having to constantly reboot just to go to the next step was never an advantage.  The real advantage of a dual-boot or multi-boot is to provided a quick workaround if a PC crashes because of a software glitch.  It was much faster than restoring from a backup either kept on or off site.

---

### Post by oldefoxx on 2010-03-25
I posted some stuff for a time on the VirtualBox forums, partly because I found their bug reporting method somewhat difficult to use.  There were several reasons for trying to report a bug, or in one case, a  critical error that concerned VirtualBox.

Anyway, the outcome at present is that if I limit myself to just the provided virtual hard drive, I can install Windows 2000 Pro on it, no problem.  If I use a a partitoning tool to divide that one virtual drive into several partitons, then try to restore Windows from a backup, it won't boot, and efforts to patch it or try to reinstall Windows to more than one partiton, I run into all sorts of problems.   When I thought I finally had it right, that it would load and run this time, I got the critical error from VirtualBox.

No big deal, as I am probably going beyond expectations for VirtualBox.  Much of the problems with Windows 2000 Pro are probably steeped in its lack of native recognition of LBA for large hard drives, and efforts work around this by Bart's PE method or Nlite have not gotten right down to the Registry change needed to add and set a ket called EnableBigLba.  It has to be enabled from the very beginning of the install process, or Windows will screw up the partition it is placed one.  You could use a small hard drive and get it on there, then set up Windows 2000 Pro to work properly with large drives, but getting a boot version on a large hard drive directly is virtually impossible, though technically within scope.  This is because the fix for Windows 2000 is in SP4 or the USP5.1, but these are not applied until after the install phase.

You can get Windows XP with SP2 to install on large hard drive, because it has the fix as well, and it is applied before the install phase.  Lots of people would feel that if you can go with Windows XP, why insist on or settle on Windows 2000, which is somewhat older?   Call it personal preference.  I've outlined my reasons before and they haven't changed.

So I can install a Windows 2000 backup onto a partition on a large hard drive,  and work out how to boot to it, but I cannot boot to it and get it to work properly on that partition until I make a change to the Registry, and with Windows, your tools are Reg.exe, Regedit.exe, and regedit32.exe.  Each of these deal with the Registry files found on the %SystemRoot%, or System partition.  I'm tinkeringaround with the prospect of moving key files from a 2K partition to a XP partition, then running the 2K Regedit under XP and see if it dredges up the 2K view of the Registry, even letting me export it if I choose.  Since XP changed over to a different manner of storing the Registry in what they call hives, the two probably can exist side by side in this manner.

In fact, I seem to recall one instance where a prior install of 2K still lived in \WINNT and a replacement install of XP lived in \WIBDOWS.  And from another period of activity, I ended up with multiple folders named \WINDOWS, WINDOWS.0, and WIMDOWS.1.  In fact, on re-installs, you tend to see User Accounts under Documents and Settings that use a shortened version of the under name for an old account and a new account with the long version of the name now set up 

Now you would be right to ask, where does Ubuntu, even Linux in any form, fit into all this?  Excellent question. amd a deserved one.  Well first, Ubuntu is my host of choice, and VirtualBox has been my medium for including Windows back as a guest.  And I admit, it is not likely to be the best you ever got involved with.  o why not discuss the ins and outs of following this course?


but there is another thing.  Linux, expecially those in he LiveCD versions, are a great deal friendlier to work with than Windows ever was.  Fixing Windows with Windows is tough, but might it not be somewhat easier going at it from another side?  For instance, gparted.iso is a great tool for handling drives and partitions, and does not need to be installed first.

But it can go further than that.  Here I am struggling to see how I can get Windows XP to serve as a platform for getting into the heart (or stored memory) of a troubled Windows 2K install.  That approach could work, but might not be the only or best way.  See, everything retained about an installed operating system and many applications are retained in certain files, located in certain specific folders.  But folders and files can be accessed via other means.

Now here is a rather interesting example.  Trying to explore the subject of the Registry further, I was lead to this site:

[http://en.wikipedia.org/wiki/Windows_Registry](http://en.wikipedia.org/wiki/Windows_Registry)

Mid-way through the reading on that page, it made mention of a open source **Offline NT Password & Registry Editor**, and provided this link:  [http://pogostick.net/~pnh/ntpasswd/](http://pogostick.net/~pnh/ntpasswd/).

Now this link takes you to a place where they are focused on using Linux as a base for getting into a Windows install and recovering or replacing the password via the Registry.  It provides downloads, source code, and an explanation of what you have.  Now if you can get into the Registry in this manner, there is no certain reason why you can't go beyond just dealing with passwords, right?  It could be a starting point for another approach entirely.

I guess you could say is that in my book, it is not so much about Ubuntu or any other OS as it is about just looking at how the separate parts can be made to perform well together.  Too many people are heavily invested in Windows, and to me that reads as meaning that it would be best not to ignore them.

But do I go to to a Windows forum to talk about Ubuntu, to a VirtualBox forum to take about my choices for host and guest, or come here discuss all three together?  I pretty much decided on here, on the chance that you already know Windows, are somewhat interested in Ubuntu, and might be open to the whole idea getting them together in one box, uh, of course I meant PC.

---

### Post by oldefoxx on 2010-03-29
I finally had to concede that maybe Win2K is not the way to go here.  I dropped the use of Ubuntu and VirtualBox to limit the scope of involvementg and tried to restore the backup to two FAT32 partitions that I set up for that purpose.  Same range of problems, so it was really a matter of dealing with an older version of Windows with a new chipset and large hard drives.  Windows 2K just would not get beyond a BSOD, even if I made an effort to repair it from an install disk.  Haven't exhausted everything for sure yet, but my brother-in-law is getting testy about why it is taking so long to get his wife's PC in order so that I can return it to her.

I was able to install WinXP, but it does not really replace the Win2K.  There is a small degree of overlap with the folders Program Files and Documents and Settings, but Win2K goes into folder WINNT and XP goes into Windows, or Windows.0, or Windows.1, depending on how may installs are  installed using this approach.

Windows XP with SP2 or SP3 does boot up after the install.  The XP install does not effect the leftover Registry settings from Win2K, and you can run the old 2K Regedit version by specifying a path to it, which would be \WINNT\regedit.  To run the XP version of Regedit with the hives being the Registry, you just enter Regedit or run the one found in \Windows, which is pretty much the same thing, since that is where the Path= points.

There are several aspects of Windows (2K or XP) that are left behind by a reinstall.  One is Registry settings, doing a \WINNT\registry -e oldreg.reg, then another of using the command line to get into the XP Registry by typing regedit, then seeing if we can import all or part of oldreg.reg.  It does seem to process through the oldreg.reg file, but then tells you that it failed, because some of the keys and values are already in use.  So did it take or not?  Hard to say.  In fact, you try to research what is said about XP Regedit, and you find that the preferred or desired method is to use Restore and restore to a previous restore point.

One of the quirks of Windows has been its manner of adding new users to the PC by creating more folder branches under Documents and Settings.  Your old settings and savings have not gone away, you just have to go up a different branch of the Doocuments and Settings where your old account has been rendered under a variation on the previous name used.  Tracking from there out to the individual subfolders, you can find old documents, links, and other entries, and any subfolder's contents can be drug into the branch structure for your current login, or any other account that you can access.  Which is likely all of them.  How can you find out which is your present account?  Use Start/Run/Cmd and see what your displayed current directory that preceeds the cursor tells you.  Or get conformation by then typing Set and seeing all the settings set up in the present environment.

These things make Windows both different and a challenge.  You can like Windows on the surface because it is what you know, but underneath it presents a ton of issues and unknowns to resolve.  You are probably just lucky that the OEM for the PC you got had to pay someone else to work out all the snags of getting Windows to install and work right on that hardware, and then adding some of the applications as well, even if just on a trial basis.  Trying to move to a later machine, but lug along a copy of an older version of Windows with installed applications can be a real problem.  Fresh installs go well enough, but to move everything from an old Pc to a much newer one?  I haven't found the magic button yet.

What I am doing is setting up Ubunu again on a couple of other partitions then adding all the updates to each, then adding the latest version of Sun's VirtualBox on top.  I backed up my two working versions of WinXP partition to an external hard drive, used gparted to set up just two 95 GB partitions on the 190 GB virtual drive I set aside.  It took about 4 hours to back up the two FAT32 partitions, only 30 GB each, and it taking about 18 hours to restore each into its own 95 GB partition on the virtual drive because Acronis' is having to convert each 30 GB to 95 GB.

Yet to be seen if if either will then be bootable, or what it will take to make XP get the job done for me.  Suppose it fails?  I will just set up some plain vanilla versions of WinXP and Office Suite, then move user contents over from the backup.  She can either settle for that, or go with the two installs of WinXP that also show up in the Grub menu.

Once the new PC is in her hands, I will take the old one, make sure that it's Win2k is updated to at least SP4, make sure the EnableBigLba setting is set in the Registry, do fresh backups of her old machine, likely use Convert to move from Fat32 to NTFS, then move the whole process over to one of my PCs and see what I can do from there.  It may be a fact that Win2K just won't go, and WinXP is not a exact or perfect replacement, but I haven't really proved that one way or the other yet.  She will also expect me to purge her old machine and leave it so that she can give it away to someone else in the family. 

Good thing I don't work for a living anymore.  I might then count up the time expended and think of the lost revenue involved.  This way it is just dead time, and at my age the word "dead" takes on new significance.  Not that I wouldn't work you understand, but the choice is not entirely in my hands.

---

### Post by waynefoutz on 2010-03-29
My wife insists on Windows XP. She will not use Ubuntu, no matter how hard I try to steer her in that direction. The kids have electronic toys that plug into the PC and require a piece of Windows software called "Leapfrog" which I can't get running in Ubuntu with WINE. Flash is another issue. She's one of those that sit on facebook all day mindlessly clicking away feeding imaginary fish and managing imaginary farms. The Linux version of flash is still buggy on those Facebook games, the cursor is slow and unresponsive. I even themed Ubuntu to look EXACTLY like her normal desktop. Bottom line is Linux just ain't for everyone. Personally, I think Ubuntu is just more fun to use than Windows, but not everyone shares that opinion. I'm a truck driver, which means I'm gone for days at a time. I did keep her computer dual booting, just in case something happens to her Windows install, which happens quite often, the Ubuntu is there until I get home to make repairs.
 Different people have different needs, that's the bottom line. I have a daughter that lives 2000 miles away whose husband enjoys going to questionable sites, and kept getting the computer infected, so she took to the Linux Mint disk I mailed to her like a duck to water. But if they want Windows, just install it for them natively. But there's nothing wrong with tucking an Ubuntu install on the side, just in case.

---

### Post by Steven_S on 2010-03-30
Well, I admire your tenacity, and I'm learning some things in the process as well (not that I get it all - just some basics). 

I do wish for you to get it to work, and I hope the solution will stand for a bit and does not come tumbling down the first time the recipient wants to install some piece of software on it. 

It's a good thing you do this as a hobby. I would already have said something like "Windows won't work on this thing anymore. Either get Linux or get a new system." :-).

---

### Post by oldefoxx on 2010-04-01
Thanks.  It is pleasing to know that some find this topic of some value or interest.  And actually, I have made a lot of progress, but there always seems to be at least one more little thing that mars the final picture.  Let's see where where we are (or I am)right now.

First, I am using the PC in question right now as i write this.  It is with WinXP installed in place of Win2K, and that is okay, though not what I had in mind.  My wife complains that her PC is showing problems with the Ubuntu + VirualBox + Win2k combination and wants me to finish up and get back to it, but some of the faults seem native to one of the three and not in my scope of knowledge to address.  For instance:

Under Ubuntu, you leave to keyboard alone for awhile, it goes to sleep and screen updates stop.  This effects VirtualBox and Windows.  Now under Ubuntu, you just use the shift key or have the mouse move a bit, and it wakes up.  But taken down to the VirtualBox and cleint level, you have to discover some new method to wake it up, such as using the mouse to force a screen size adjustment (the host key combos do not work either).

VirtualBox is very workable, but it limits you in some respects.  A virtual floppy A Drive, local C drive. CD-ROM D Drive, network sharing, serial port, and either USB or shared folders for just about anything else. I pushed the limits when I tried to partition the virtual C drive, but it took surprisingly well.  Only not completely.  VirtualBox has a problem with dealing with the partition table and designated boot process when restoring from backups, which I could only overcome by doing a reinstall of the OS.  Turns out this does not work for Win2K, but WinXP is capable enough.  Yet Win2K works fine on its own if installed without the partitioning.  The gain is not all WinXPs though, because it failed to let me access shared folders.

Working in this mode, the real problem area is Windows.  No LiveCD option available for Win2K, though the BartPE process can render one for WinXP, but limited in what it can do.  WinXP with SP2 or SP3 slip-streamed into the install disk can use LNA to access large hard drives, but nobody apparently has gotten Win2K to install with LBA working even with SP4 or USP5.1 applied.  It has to work instantly, because otherwise the Windows installer will screw up its read of the large hard drive partition tables.  You could have a small drive for the initial install and work from there, but how are you going to manage that under VirtualBox with its one local C drive?  I guess I can't fault Windows, because it was adequate for its time, but it was really abandoned except for security patches in the constant search for new sales.

That's not much to fault Windows for, but let me add these shortcomings to the mix, and if you have had to deal with any, you can understand the frustrations involved.  First, reliance on drive letters to designate each drive.  Second, the lack of a truly uniform manner in assigning those drive letters per drive - I've run into situations where the BIOS, the Windows Installer, and the final Windows install each used a different manner, and this is on the same machine!  Now it is true that the Administrator can use Disk Manager to reassign drive letters by swapping them around, but often the most critical change is for the system partition, and you cannot change that, ever.

When I set up three partitions on the virtual drive, they were designated C, D, and E, and that was ideal.  The backups restored to the correct partitions with the correct drive letter.  But none would boot.  Some conflict that VirtualBox is unable to resolve at the moment.  So I try a reinstall, but now my partitions are lettered C, H, and I.  What happened?  The Windows installer decided to include the USB-attached devices, what people call smart cards, and these four took up the letters D to G.  Not my choice, and no way to exclude it from happening.  People like USB devices stealing letters in the sequence because they can use this for a way to get a PC to boot from an attached drive when it suits them.

Here is an oddity that I can't really explain.  I can understand that the host, Ubuntu, is aware of the smart card devices, but under VirtualBox, these are not even offered as options for inclusion or exclusion with regards to the client.  So how did the WinXP installer have access to them?  After you get the Windows installed, you can see it stop four times on boot up to request media to be inserted in each device in turn (this should be a no-no), and I can use Admin to go under System/Hardware/Device Manager and disable the four, but they have already spoiled the game with the device re-lettering that they caused.

You wan to know the real difference between pursuing Windows and going with Linux is?  Things like this, that with Windows, will never be addressed and fixed.  You move up a notch or two, at your expense, and hope that things like this got taken care of in the new version.  Only how can they?  Does the vender actively seek problem reports or make it easy to contact them?

And there will always be something to pester yourself about, but don't worry.  There are more versions to come.  Just wait a few years.  Now with Linux, whatever distro you go with, things are changing and improving all the time.  I still use Ubuntu 9.04 mostly (generally fewer follow-on problems), and at last count there were 284 updates there online to download and apply.  And that is in one fell swoop, not dishing around with a few here and there and constant reboots as happens with Windows.

Most of the so-called fixes for Windows just go after ways that hackers can get in, and in my opinion, serve more to protect the reputation of Windows in general as being secure than to make it really work better.  There are of course a few exceptions, such as DirectX (make Windows more appealing to game developers and players), and Media Player (everything has got to look good, you know, and easy enough to use).

Yes, I would like some changes or fixes in both Ubuntu and VirtualBox.   It would really be helpful in some places.

But I am fed up with bug reporting.  You spend more time trying to find out how to submit a bug report than should ever be necessary, on top of which they want you to research existing bug reports and see if it has been reported before by someone else.  If you find a match, they don't want you to open a new bug report, even though some aspects of it may differ in significant ways.  And it might even show the extent of which some bugs are found to be prevalent.

Then for months afterwards, you get an email reference to your bug report, many which say nothing (inbox to outbox flow, at least it crossed my desk), until some dude out there indicates that it should be tossed because you did not do it exactly to form (what form?  No examples were ever noted), or that in his mind it is neither important or significant enough to go with it any further.  And don't you love it that you are the one that is suppose to identify the package that is at play here?  Like how should I know?  It just happens.

So they are in overload.  I can understand that.  I'm loaded up too.  But why all this stuff about how to report or whether it was reported correctly, when all I was trying to get across is that something happened, and what i can tell you about it.  So to save some time on both ends, I will just report it on forums like this, and leave it to chance if anything further comes of it  I don't need months of getting little tickler emails until someone decides to squash it.  And i care less what hands it goes through or what others do with it, I did my part if I just get the word out at the start.

So, with all that in mind, let me just add this:  The word is out now.  At least as far as I am concerned.

---

### Post by oldefoxx on 2010-04-09
Well, a bit of good news at last.  I've been handling some of my CDs so much lately that they've become undependable, what with all the skin oil and fingerprints that they've gotten.  So I put warm water with dishwashing fluid in the sink, bathed a batch,rinsed them thoroughly, and laid them out on the countertop on some drying towels before gathering them up and putting them by my PC.  Occasionally one will still produce and error, and if I look at the record side, it likely still has a fingerprint or something on it.  Helps to wash your hands thoroughly first too.

Got Win2K back on my in-law's PC, but Office 2000 turned out to be a whole new problem.  However MS screwed this up, they tried to fix it first with a Service Pack 1, then pulled that back and had you go with a Service Release 1, which had to be followed with a Service Release 2.  If you have SR-1 and SR-2 both installed, then you can move on to Service Pack 2 and up the list of updates.  There are three pages of updates shown on the MS site, but no direct way to get there.  I basically start with home page, all products, Office, and then get to Office 2000.  There it lists what just pertains to something like Word or Excel.

Trouble is, Office is somehow funky when it comes to what it has on it.  With some of my disks, it wants to skip SR-1 claiming it is already installed, only to balk with SR-2, which wants you to go back and add SR-1 first.  SP2 won't install until you get the other two straight.  And it can take hours going through a stack of old backups of installed disks looking for the right Office one that will take SR-1 after you install it. So in its own way, Office can be as much or more a problem than getting the operating system on.

You see how easy and peaceful it would all be if people would just learn to use OpenOffice instead?  You download a Ubuntu distro, you burn it to CD, you boot from it, you decide to install it, and you just move to it in place of what you had before.  But no, most of you have some cherished reason for wanting to stick with Windows, which can be a horror to deal with, especially with new hardware involved.

Back to the bit of good news.  Could not stay on Windows XP with in-law's setup because of that total irritation of having to deal with the authentication process.  It finally reared its ugly head, and here is no good fix for it, so back to Windows 2000 instead.  And Win2K installed without a hitch.  But got stuck with Office and the SR-1, SR-2, and SP2 problem.  So I decided, hey let me just make a backup of my laptop, then see if that will restore and run on the in-law's PC.  So I did.  Takes forever with True Image under these conditions, and I had to already have Windows on the guest virtual drive and install True Image there so that it would be able to recognize the external hard drive (True Image doesn't see it through VirtualBox alone), but it ran to completion.

Only I got a BSOD from Windows when I tried to boot it.  Flawed again, right?  Not exactly.  It got halfway down the progress bar with the Windows identifier screen up before it died, and that is usually far enough to signify that a Safe Mode boot will work.  And it did.  I put the problem down to the fact that the chipset drivers for the laptop are totally incompatible with the chipset in the desktop, went into Safe Mode with Networking, got that up, then went to find the G33 Express chipset drivers that previous research had shown were needed for the in-law's PC.  Found them, downloaded, but the video driver failed to apply.  The default screen size was only 640x480 at 16 colors, and that did not cut it as a minimum.  Ran the GuestAdditions for VirtualBox, got up to 800x600 by 16 colors, and this time the G33 Express chipset drivers were able to install.

The little bit of research I tried on the partitioning and booting conflict seems to lie in the fact that both the partitioning table and the boot sector want the same space.  How they get around this with real drives is another question, but it just indicates that the two do no fit together on the virtual drive.  Seems a shame though.  I thought I was onto something really good.

So what is left with my in-law's machine is to clean off my junk and add in what she wants.  That is assuming that I don't somehow mess up again.  What I have really learned is that if you are insistent on trying to stick with outmoded operating systems and somehow get them onto newer hardware, then you best be thinking along the lines of using something like Ubuntu and VirtualBox as a means to creating a structured space for your choices to run around in.

Let's see.  I've discussed the lockup situation under the VirtualBox client that somehow seems reflective of a screen hang problem under Ubuntu.  Be nice to see that fix.  I'd even consider a different host if it got rid of that particular problem.  What else is there?

Oh, since the guest only sees other devices through the interaction of VirtualBox with the host, some odd situations come up.  Ubuntu has to scan the removable drive or CD and display a window with some of its contents before VirtualBox can access it and hand it off to the client.  Windows in turn scans all drives before you can access any of them, so you can get into a situation where it could be ten or 15 minutes before Windows can go forward.  Even longer if you are using very large hard drives.  Bad design on Windows part.  More evidence that just going to Ubuntu might be better.

Worse, you can be working under Windows, trying to use the CD drive,
and get entangled.  By this, I mean that Windows cannot unmount or eject the CD on its own, that has to be done by the host.  But if you try, you will still see the old CD figuratively mounted by the host, and you cannot mount or access a new CD, and if you try either a mount or unmount or eject, you just see messages back that this cannot be done.  In a few cases, I got around this by shutting down the client and VirtualBox.  In other cases, it was bad enough and would not clear until I rebooted the host as well.  That is very disruptive to current tasks that might be underway.

---

### Post by oldefoxx on 2010-04-12
Here is a new one for many of you.  Slipstreaming.  You take an original install disk for some version of Windows, and using a provided process, merge later patches into it so that what you now install is an already upgraded version of that Windows.  There are several places on the internet that provide instructions, but some are a bit confusing to follow.  And they may miss out on an important detail or two.

Anyway, I've done this for Windows 2000 Pro a number of times, upgrading the install to SP2 or SP#, but I never got SP4 in exactly right.  
wasn't sure why that was.  But I've had a lot of problems with CDs lately,
having tried to clean and use some a few times, and it was only the original that was left untouched.

So I looked for Windows 2000 sp4 slipstreamimng agan, and tried to follow the process outlined exactly.  But instead of immediately burining it to CD, I had VirtualBox access the ISO as though on CD to see how it ran there in a client space.  Had the same problems as before,asking for a floppy with SP4 to be inserted in the nonexistent A: drive,  but there were two files that had not been copied onto the CD image because they were unmentioned, so I added them to the image and that took care of it.

And the surprising thing is, that Windows 2000 Pro with SP4 already incorporated had no problems installing and running in a client space where Windows 2000 Pro with just SP2 or SP3 had failed to boot, but hd died with a BSOD.

Now to mess around with images like this, I needed a burn package and an ISO editor.  Brasero works find for the burn, even reading a CD and putting an image of it on the hard drive to be worked with. but I was not sure about an ISO editor.  What I found is that there is an ISO Master for Linux out there, so I got it, added the required packages to Ubuntu to compile it, did that and got it installed, and it worked just fine for adding and deleting files and folders to the image.  I figured this was worth passing along.  Brasero now permits that image or any other to be burned to CD, so I made four copies on CD.

I guess I will have to install Office again, but I had noted a link on the site related to slipstreaming that mentioned Office, and I am going to check it out first.  I just might be onto something here.

ISO Master is clumsy, in that the info about which displayed field holds what info is not apparent, but in general, the large field in the topmost section is the files and folders being seen at the current hard drive location, and the large filed in the lower section is the files and folders found in the image being worked on.

---

### Post by oldefoxx on 2010-04-13
Wasn't up to snuff today, and mostly slept.  Got into looking at the whole question of slipstreaming Office 2000 as apparently possible.  Found numerous links, two methods, one is to essentially duplicate the manual method for slipstreaming Office XP.  They claim it works, but I could not work out what to do here or there when I god different results.

The second method turned out to be a whole lot easier.  This lead me to a free download of a program called SlipStreamer that supposedly will do all flavors of Office and all flavors of Windows, and was extremely simple to use.  It seemed to work fine.  I could have done a series of hotfixes with it as well, but I hadn't gone that far ahead in my planning.

Let me just make this point again.  Old versions of Windows do not mate up will with advance hardware, but they can serve well enough if only a client under a different host OS and a VM manager.  Tools used to backup and restore images may have a problem when just dealing with the client, but give it real thought, because another approach may occur to you.

Something that would be real helpful at this point is a way to access the client's vertical drive and contents from the host side. Havn't seen anything of that nature yet.  Puts pressure on to either relate between the two sides with external drives, or create temporary connections via shared folders, or something like that.

With older model PCs, there is no pressure to move off of any given OS,
but I can see where that changes with newer PC designs.  Youe choixw of what to do next might depend largely on where you are now and what you feel you might need, either now or next.

My wife has gotten more comfortable with the Ubuntu + VirtualBox + Windows 2000 blend.  One problem that came to light is that she would press the F key before finding and pressing the designated host key.  That does not work.  You have to do it with the host key first.  She blaims me, because she thinks I instructed her otherwise.  Not on any day of the week, because that is a key known fact.  But you know wifes, they hate instruction from their husbands, and then it is your fault anyway if they somehow got it wrong.  Oh well.

Enought for the day.  I'm gone.

---

### Post by Elfy on 2010-04-13
There used to be a windows sub-forum here - which is where this should be. 

Thread closed for staff review.

---

