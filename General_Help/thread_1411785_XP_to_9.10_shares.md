---
title: "XP to 9.10 shares?"
date: 2010-02-20
forum: General Help
---

### Post by Tourdog on 2010-02-20
I can look at my XP files from my Wubi Karmic with no problems.  It would seem with the mix of file systems on my hd that from XP I should see my Karmic shared files.
What is up with this?  It would be great to have "read/write" both ways.

tourdog@PJK3:~$ sudo fdisk -l
[sudo] password for tourdog: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15108   121354978+   7  HPFS/NTFS
/dev/sda2           29248       30401     9269505    c  W95 FAT32 (LBA)
/dev/sda3           18336       29247    87650640    5  Extended
/dev/sda4           15109       18335    25920877+  83  Linux      ext4
/dev/sda5           18336       28797    84035983+  83  Linux      ext4
/dev/sda6           28798       29247     3614593+  82  Linux swap / Solaris

Partition table entries are not in disk order
tourdog@PJK3:~$ 


Nautilus and Samba are running on my Karmic.   What am I missing over on XP that precludes seeing my Karmic shared files?  This has been answered here but I cannot find it (search).  :confused:
TIA!

---

### Post by gsparky2004 on 2010-02-20
Okay, grab a cup of coffee.  Your questions will require some explanations:

To start, look at the results of your "fdisk -l".  If I understand your set-up correctly, you have a dual-boot system with XP and Karmic.  Your partitions are (in order they were printed):
- sda1 = NTFS:  This is your XP partition.  
- sda2 = W95 (FAT32 - LBA):  This is probably your "recovery" partition.  I'm guessing you have a Dell computer?
- sda3 = extended.  Probably for file and data storage.
- sda4 - 6 = standard Linux install (boot, root, and swap).  

First question:  Why won't XP see your Ubuntu partitions?  That's because XP is Microsoft, and it has issues seeing anything other than NTFS.  I imagine that there are ways to (special programs, perhaps?) that will allow XP to "see" your Ubuntu partition.  But I've also had issues where it would not "see" anything other than itself.  Hey, it's Microsoft!  If you've not been assimilated into the Borg, it doesn't see you!

Second Question:  Why won't Nautilus work?  Nautilus should allow Ubuntu to "see" your XP partition.  It might not until you actually mount it (see below).  

Third Question:  Why won't Samba allow it to work? Samba is for *networking*.  And since you can only have one OS (XP or Karmic) running at one time (you can't have both working at the same time), Samba won't do you any good.  If you had an XP machine *on a different computer* running, then Samba would be able to help.

Still with me?  Good.  Let's move along.  If you want to set-up a shared drive, I suggest that you just mount your XP partition under Ubuntu and keep any files you want to share on the XP partition.  The way I worked it on my dual-boot XP / Karmic system is that I automatically mounted my XP partitions on my Karmic system.  Then I created bookmarks for each of my primary directories (My Documents, My Pictures, etc) under Ubuntu.  I just keep all of my files under XP; that way, it doesn't matter that XP cannot "see" the Ubuntu partition.  I even have Thunderbird (2, not 3 because 3 still seems to have... issues) on Ubuntu using the exact same files on XP.  Never have to worry about syncing them because they are synced by default.

If you want to mount your XP partitions permanently under Ubuntu,open a terminal and do the following:
```
cd /media
sudo mkdir sda1
sudo mkdir sda3
```
This creates two permanent mount points that you'll use to allow Ubuntu to "see" your XP partitions.  NOTE:  I didn't create a mount point for sda2 because that's your "recovery" partition and you probably don't want to mess with that.
Next, open your /etc/fstab file so that you can edit it.
```
sudo gedit /etc/fstab
```
At the bottom of the file, add this line:
[B]/dev/sda1 /media/sda1 ntfs nls=iso8859-1,gid=tourdog,uid=tourdog 0 0
/dev/sda3 /media/sda3 ntfs nls=iso8859-1,gid=tourdog,uid=tourdog 0 0[/B]
Save the file and exit.  Now, restart your system.  When you open your "Places" menu, you should see two entries (typically under where it says "Computer") that are your "connections" to your XP partitions.
If you want to create bookmarks for "My Documents", etc, go to the sda1 (which is probably named "XX GB filesystem" or some such), and drill down to "My Documents".  It's probably "Documents and Settings" -> "Owner" -> "My Documents".  Once you have the "My Documents" folder open, click "Bookmarks" on the top menu, then click "Add Bookmark".  

From now on, just use the folders already under XP (or create new ones) and just keep your files there.  That's my suggestion.

If anything isn't clear, let me know.

---

### Post by Tourdog on 2010-02-20
gsparky2004,
Thanks a million for the extensive work you have generously provided!!!

My HP system works extremely well........   from stone cold it is a 50 sec bootup for Karmic and a 15 sec shutdown..........  and very fast and you can see it is very old (6 years).   1 clk on Places/ My HDD and sign for authenticate/mounting and my whole C:\ is there........   I can instantly play my Music or read Docs from those extensive NTFS files all the while being in Karmic.   TurboTax and maybe Delorme/ Garmin mapping are the only reasons XP still exists for me.  My 64 bit Karmic is rippin good and very fast. 

 Now, for those times I am "over" on the XP side I would like reciprocity to "see" ie at least "read" my "ext4" files ie Karmic.

You can see >  I can look at my XP files from my Wubi Karmic with no problems.  ...............

But, if XP can only work with NTFS then the "BORG" that I have been flirting with since 1985 have got me ..................  :confused:    Wine or VB seems beyond complex at this time.

> First question:  Why won't XP see your Ubuntu partitions?  That's  because XP is Microsoft, and it has issues seeing anything other than  NTFS.Ratts!  Someday but apparently not yet.

---

### Post by gsparky2004 on 2010-02-20
You're quite welcome, Tourdog!  I hope I was able to help.

I'm with you on the startup / shutdown.  I have an 8 year old Gateway P4 (single core) that is also roughly 50 seconds from power-button-to-mouse and about 30 seconds (which I believe is due to my extensive use of network shares, which requires a lot of "I'm going away!" messages on the network) for shutdown.  I got serious with Ubuntu when I realized it was (literally) taking 7 minutes for startup on my WinXP.  Sometimes, even longer.  Really, MS, are ya kiddin?

And just like you, I only keep the XP around because of a few things I need.  However, most of those I've now ported over to a virtual machine running under Ubuntu.  I'm using VMWare Player, which is working out quite nicely.  

As for your desire to read/write to your ext4 partition from XP, a quick Google search showed me lots of stuff for accessing ext2 and ext3 from Windows, but I couldn't find anything for ext4.  Again, for now, I suggest just keeping everything under the XP partition and everyone's happy.

---

### Post by Tourdog on 2010-02-20
Well done gsparky2004!  Thank you again !!!  The XP partition for now and watch for the morphing of  Wine and/ or VB.

---

### Post by kazakore on 2010-03-14
OK wanting to do this myself and searching here and Google seems to imply I should see my hard drives/partitions in the /Dev folder. Well I don't seem to, I have no SDA# or HDA# files or folders in there.

Where do you put "fdisk -l" to get the list of partitions? Tried in Root, Devs and Media with no joy.

Using US9.10 if it makes any difference (says in my profile anyway.)

---

### Post by oldfred on 2010-03-14
We tend to post terminal commands as they can easily be copied and pasted into a terminal session, results can then easily be pasted back. Applications, Accessories, terminal 
If we tried to use menus, they cannot be copied and it often gets confusing but just about everything can be done either way but with different views. Terminal is alway text.
System, Adminstration, disk utility will also give info on drive and partitions.

---

### Post by Tourdog on 2010-03-14
Oldfred,
Thanks (as always) very good info (explanation)  :)!

---

### Post by kazakore on 2010-03-14
Thanks Oldfred.

I was typing in Terminal. Must of just been blinded by having to go to work on a Sunday I guess. Once I looked in the Disk Utility and saw the disk was called sda I immediately saw it in /dev (although I did look for sda and hda) and then also realised I was missing /dev/sda off the end of the fdisk command, as you obviously need to tell it which disk, rather than try and do it from the root of a disk you can't find.

Anyway seems to be working now, no more putting in password to access my mounted drives (and strangely also not having to for a couple I haven't permanently mounted.) Just a couple more tests to do, most important is I can access it from within Renoise without having to go mount it each time.

Thanks again.

Oh and be warned. I put one for my Windows drive as well as my Data drive as have a few bits on there (and thought it may make using stuff through Wine easier.) I had forgotten to create a directory for this first though and it caused by computer to use 25-30% on all four cores (Xeon Core2 series, 2.83GHz.) A little thing like that can cause your system to use stupid amounts of resources for nothing!

---

### Post by kazakore on 2010-03-14
> **gsparky2004 said:**
> 
- sda3 = extended.  Probably for file and data storage.



Not that it matters but it might interest you or others for future reference but I noticed this Extended is actually like a virtual drive and the Linux Logical Drives are within it. If you look at start and end addresses you will see they match one of the Ext4 and the Swap drive start/end. It's not a discrete space itself.

EDIT: It does actually matter for this thread as what I've just pointed at quite strongly hints that Tourdog probably doesn't really want to/shouldn't mount this as a drive...

---

