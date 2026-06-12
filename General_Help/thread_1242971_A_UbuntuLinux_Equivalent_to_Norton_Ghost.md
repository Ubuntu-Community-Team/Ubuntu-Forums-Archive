---
title: "A Ubuntu/Linux Equivalent to Norton Ghost"
date: 2009-08-17
forum: General Help
---

### Post by Inquisitive1 on 2009-08-17
Is there a_Norton Ghost_ equivalent in Ubuntu?

---

### Post by slakkie on 2009-08-17
[www.clonezilla.org](www.clonezilla.org)

---

### Post by RedSingularity on 2009-08-17
+1 for clonezilla.  Works great!

---

### Post by jerrrys on 2009-08-17
another vote for clonezilla, been using it for 6 months and it hasn't let me down yet

---

### Post by skirkpatrick on 2009-08-17
I like clonezilla.  There's also [Ghost4Linux]("http://sourceforge.net/projects/g4l/")

---

### Post by metalf8801 on 2009-08-17
defiantly Parted Magic 
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by HermanAB on 2009-08-17
Hmm, being an old curmudgeon, I simply use Data Definition 'dd'. Crude and simple.  

If it was good enough for my granpaw, it is good enough for me - Now get off my lawn!
;)

---

### Post by eldragon on 2009-08-17
noone mentions dd?

---

### Post by Sean Moran on 2009-08-30
Thank you for the recommendations of clonezilla - I am currently doanloading an .iso to try it.

It may do the job required in a roundabout sort of way, although I am intrigued by the mention of 'dd' also, as there might be a more efficient way to achieve the result I am trying to find a way to do these last ten days.  It's time to ask for some tips, as once again I maybe overloooking something obvious due to being 'stuck-in-my9x-ways',

I notice that this thread is a week old and don't mean to run too far off-topic, but it seems more appropriate to continue from this thread than to begin a new thread on a different way to achieve the same thing.

Briefly, I have used a simple system for backup/restore of the old win9x systems for the last decade.  Step by step, as follows:

**Create zip archive - **

1. Install fresh installation to C:\ from CD. 

2. Setup standard applications.

3. Configure system, desktop, menus, panel, (move win386.swp to another disk partition), and application positions and preferences.

4. Copy C:\WINDOWS and C:\Program_Files to a new directory on another partition.

5. WinZip the new directory into an executable zip file.  

6. Store that new .exe zip file on the D: 

Then, at the end of each month (this was win9x - the o/s with the 30 day use-by limit) , or if something should go wrong with the running distribution, the restoration procedure was a ten minute job:

**Restore Archive - **

1. if suspect virus, reboot in DOS and fdisk /mbr to clean Master Boot Record (removes GRUB/lilo unfortunately), and format C: /s and THEN unzip a 16-bit (8.3 DOS files) mini installation before:

2. unpack the stored system onto the C: partition.

3. if newly formatted C: partition, copy new msdos.sys file onto root dir. (attrib req.)

4. if exists, rename the old WINDOWS dir WINGOES and rename the new dir WINDOWS and reboot.

5. delete C:\wingoes and run defrag.

That is how I have been managing to keep the old systems in good shape for the last ten years, but Ubuntu is a different kettle of fish altogether.  

Ubuntu has been quite happy to run perfectly from install and isn't as likely to need periodic re-installations nor suffer from malicious attacks, but it is about time I learned how to replicate a similar sort of operation with Ubuntu although the reasons are more optimistic:

1. Personal Use: backup and restore a newly configured Xubuntu or Ubuntu installation across HDD partitions, ie. archive /dev/sda6/* to /dev/sda7/backup.iso or equiv.  Reformat /dev/sda6 and then unpack the archive back onto the newly formatted drive.

2. Share with friends: I would also like to be able to install a custom (aka UCK)  .iso image on CD, DVD, and on my USB stick, the idea being a standard sort of Ubuntu or Xubuntu distribution, but with standard configurations and local settings implemented.

---o0o---

At this stage, I have been trying two different software application packages:

Ubuntu Customisation Kit (UCK) has been successful in making an .iso image that I can then burn to CD or DVD and reinstall on another partition.  The three drawbacks are:

1. that it is slow because I haven't worked out how to use the ISOmount utility to run an .iso image that can then install onto a different HDD partition.  

2. I am yet to work out how to duplicate the original menu/panel/desktop configuration onto the new SquashFS or .iso image.  

3. it seems to have made up its own mind about some of the applications and languages and I am still at a loss as to how to gently ask the installer to look for security packages online but refer to the local disk archives repository, which I have also added to the proftpd public/ directory but not having much luck in limiting the ADSL downloads with each new trial.

UNetbootin to install both the complete system as well as the .iso image onto the 4.0GB USB stick.  This is a separate hurdle that I am almost but not quite able to overcome.

I am sure that there must be something I have overlooked here.

---o0o---

The best that I have achieved using UNetbootin has been on a FAT32 partitioned /dev/sdc1 that boots my old legacy Pentium 4 and gets to a prompt that goes - 

boot:

and when I type initrd or vmlinuz or anything I can see in the /casper directory or thereabouts, it's *cannot find* or *doesn't exist* from memory, so I must be close to perfecting the USB option, but still not quite working out what to do to complete the process.

---o0o---

The other improvement I have been considering, (although it's a long process with these continual downloads that I am having no luck in redirecting to my local repository,) has been to copy the various %gconf files within the standard user's home directory  across to another partition and then replace those in the /home/<user>tmp/remaster-root/home/<user>  during the UCK download process, (or sometime before it re-SquashFS's the system into the .iso or however it does it.  Again, I continue to seem to get close to finding a solution, but soon find myself back at the beginning to test another way, and it is the last day of the month today.  I have to fix this now or never.

---o0o---

It is a rather confusing lot of jibberish, these last ten days trials and tribulations.  

I will try to clarify the essential background information for the questions I still have, as I continue to try new methods todday, although it is not always advisable to be logged in online during a 7 hour download process, so this is a rare moment to try to ask for some advice on:

1. The final step for the UNetbootin bootstrap process where initrd.gx and vmlinuz are in the USB drive's /casper/ directory and the prompt asks me - 

boot:

2. Would this dd program be able to run on eg. /dev/sda2 and then somehow transfer or archive everything on a running Ubuntu installation on /dev/sda6 across to somewhere on /dev/sda7, then after reformatting /dev/sda6, copy/transfer/unpack everything from the /dev/sda7 archive back onto the newly-formatted /dev/sda6 so as to restore permissions et al. and given that GRUB still lists the old installation on /dev/sda6 then boot up to the same installation as what was running on that partition before reformatting?

3. How can I get the UCK and Synaptic Package manager to look for .deb packages on my local disk or ftp repository rather than download what I already have.  I have tried to use the dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz to somehow get these utilities to recognise the current repository rather than reload the same thing repeatedly, but still I am not getting something right.

These are the sorts of things I am experimenting with, and not having much luck with after over a week, I will try to get the time to clarify this later today and would appreciate it if anybody can see the obvious error in the old-fashioned way I am trying to use to achieve this system backup/restore objective.

My apologies for being obtuse.  It has been a long week.

Off to trial clonezilla.  BRB before next month.



-----oo0oo------

**04:12 GMT**

The clonezilla seems to do the job admirably, although there are a few things still to adjust before the next trial.

With the SOURCE as the newly installed and still fairly clean Xubuntu on /dev/sda6, 
and the TARGET on /dev/sdb6, it was a bit of a worry making certain NOT to re-write a new partition table on the secondary HDD target, but there are copies of 'most' data on both drives so I took a chance, and it left the partition table on the target HDD alone, (apart from /dev/sdb6), so it came through.

The funniest part was that it seemed to have somehow changed the SOURCE MBR  so that what was BEFORE the default boot drive (sda6) changed transparently to default to the cloned AFTER target drive ...

... and the clone was good enough to fool me, until I had a look through the Mount Manager and noticed that of the two partitions both set with mountpoints at / (filesystem-root) it was the newly cloned root on /dev/sdb6 that had booted by default, and I was fooled. 9-)

To know that the same installed distribution can be cloned across devices and not run into mounting problems (so it seems at first glance) is a very big step in the right direction.  Now I hope to adjust a couple of spare partitions down to a fairly compact size, because there was a message about clonezilla having success at cloning a small partition onto a larger partition, but problems in the converse, so that needs to be taken into account before attempting the restoration.  The next step is to trial the .iso option, because if that can be created from a small partition, then judging from the success of the first trial, it should make it possible to restore a freshly-installed working system on most HDD partitions in under ten minutes, and there's a fairly good likelihood that USB might work that way, which is the objective.

I'll get back to trying this out and finish up with a little luck at the end of the day.  Any 
advice on how dd might accomplish the same task would still be appreciated, although it seems that clonezilla is a very good option from what it has done so far.

---

### Post by Sean Moran on 2009-09-01
A day late but I think I finally found the solution to this filesystem archive problem that has kept me busy for almost twelve days now.  As often happens, it turned out to be a fairly simple answer - SquashFS was all it took to do the job.

Clonezilla is an excellent utility judging by the two trials I ran yesterday: firstly cloning from SOURCE partition /dev/sda6 to TARGET /dev/sdb6, and then the second test cloning another new SOURCE installation on /dev/sdb17 to a USB stick on /dev/sdc1.

Both operations went so perfectly that it took me a little while after rebooting to realise that not only did both tests work, but they also cloned the UUID of the partitions, which is where things became a little problematic for what I was wanting to achieve.  The cloned partition did such a good job of impersonating (loosely put) the source that the original partition vanished.  :confused:  (that's probably what it is meant to do anyway 9-)

Running a half-dozen different installations of Ubuntu and Xubuntu across these various partitions, means that not only do I want to be able to restore a specific partition verbatim in the event of mishap, but to install and configure a nice clean installation on one partition, with the few extra packages I tend to gravitate to, and then replicate that onto other partitions, or to the USB stick, or to a custom CD or DVD.

Still too early to test this all out and know for sure, but theoretically (in my mind anyway) it should now be possible for me to configure a nice little Xubuntu dizzy on a spare logical partition somewhere, then simply SquashFS the whole root filesystem  into a 'squashed' file in a dir on another partition, then reformat another partition, unsquash the archive into a new directory on that newly formatted partition (the unsquash utility doesn't seem to want to unsquash anywhere it can't make its own new dir but maybe there's an option I haven't found after one attempt) and then just mv the files back to the root directory.

I assume that I might also work out how to use the mkisofs utility to slim the squashed file down to an .iso image which could then be used by UCK to build the rest of the CD booting and installation capabilities that I have not yet had the time to learn about properly or test out myself, but theoretically, why worry?  

A day late but I've finally managed to copy a complete Ubuntu (actually Xubuntu but same same) distribution from one partition to another, via the SquashFS utility's magic.

I suppose the funniest part of all this is that had I simply used  **cp -p -R <source partition> <target partition>**  it probably would have done precisely what I was wanting to try out in the first place, assuming the numbers of the kernel and initrd.img are adjusted in the /boot/grub/menu.lst to suit any name changes (eg. 11-generic --> 15-generic) , I would have realised almost two weeks ago that a running an Ubuntu system on one specific partition with one specific UUID will (seemingly) work just as well if let loose on another partition with a different UUID.

This isn't quite the whole objective of 'ghost' utilities anyway (just moving dizzies between partitions on the same machine), but there are similarities in purpose between the two, and I searched for *squashfs* as well (on this forum ooking for alternate threads) but these same threads seemed to come up again, so please let the thread get back to the 'clone' operations, if at all, and I will keep further reports on any of the 'post-worked-it-out' procedures for the thread I've already begun down in the testimonials sub-forum.

This knowledge deficiency of mine would now appear to be overcome, (finally after almost two weeks of failed efforts and chronic laziness on the RTFM factor), as I have finally succeeded in moving the system from one partition to another.   With that, now things can start to get interesting, in a 'permanent' sort of way, at last.

Thank you to the developers of SquashFS, Clonezilla, and the Ubuntu Customisation KIt (UCK) because I believe that I can now incorporate those three into various parts of the system administration sorts of tasks that I have been generally doing for many years on the old FAT32 clients but have yet to try to find out how to do on the Linux desktop.

---

