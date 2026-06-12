---
title: "Automatic Ghost of Data Hard Drive"
date: 2011-04-05
forum: General Help
---

### Post by MiniVanMan on 2011-04-05
I'm trying to make a simple task as complicated as possible, so bear with me.

I'm going to force a friend onto Ubuntu soon, and the biggest requirement is photo management.  

He wants his extensive photo library backed up, and backed up some more, and then when all feels safe, backed up even again.  

Currently, all his photos reside on a 4 disk ***striped ***RAID array, based on his cousin's recommendation.  The intent was a RAID 1+0, but they failed, and that needs to be fixed immediately.

So, instead of going with more mirrored hard drives in a RAID, which I know Ubuntu will do just fine, I'd like to simplify and just do manual backups of each hard drive.

So, I'm looking for a program that could possibly be set up to automatically back up a hard drive onto another hard drive on a weekly basis or something like that.  Ultimately, doing a manual copy/paste of the data in the drive could work, but would be time consuming.  

I'm scared of RAIDs lately because of a recent fiasco with a BIOSTAR motherboard and how it set the RAID mirror on a set of hard drives for a Windows load that rendered the harddrives basically useless for anything but a RAID mirror, with that motherboard and a Windows load, and I almost lost a lot of data because of it.

I'm also not sure how well Windows would recognize a RAID partition created in ext3, if he ever wanted to go back to Windows.  

Any help is appreciated.

---

### Post by ronparent on 2011-04-06
I won't try to answer all of your questions. But if you ever want to read your raid with windows, you will have to setup a FakeRAID which is simply a software raid based on a motherboard raid chip set. Secondly the partitions would have to be formatted in a format window will read (ie NTFS or fat32 etc.). Not all MB raid sets support raid10 and some of those that do in windows do not do so with dmraid in ubuntu. Raids are inherently complicated and you should not employ them without some study. And finally, do not depend on a raid solely for backup. You might be more secure with a sound backup system not dependent on raid.

---

### Post by MiniVanMan on 2011-04-06
> **ronparent said:**
> I won't try to answer all of your questions. But if you ever want to read your raid with windows, you will have to setup a FakeRAID which is simply a software raid based on a motherboard raid chip set. Secondly the partitions would have to be formatted in a format window will read (ie NTFS or fat32 etc.). Not all MB raid sets support raid10 and some of those that do in windows do not do so with dmraid in ubuntu. Raids are inherently complicated and you should not employ them without some study. And finally, do not depend on a raid solely for backup. You might be more secure with a sound backup system not dependent on raid.

These are all the points that make me not want to do a RAID.  The Biostar board I was talking about utilized a FakeRAID, and when I set it up in WinXP, it rendered the hard drives useless for anything but a RAID install in Ubuntu (which I didn't want to do).  I wanted to run XP on one hard drive and Ubuntu on another for a dual boot, but couldn't.  Was extremely frustrating.  (Debian was fine, but Debian's partition manager is more sophisticated than Ubuntu's).  I couldn't unRAID the system in the BIOS of the Biostar board.  Cheap board, cheap BIOS.  It's whatya get I guess.  (Not the first problem I've ran into with Biostar and Linux).   

The current motherboard in question is a top end Asus board, and I've never ran into any problems with Asus boards when it comes to RAID.  But that doesn't mean I needn't concern myself with cross compatibility in the future.  These are data only drives, and I want NOTHING on them that could potentially limit another a piece of hardware or software from recognizing the hard drives in the future.  This guy isn't going to have this computer forever, but he intends to categorize and keep the hard drives forever. 

I'll still need to format the drives in NTFS because XP won't recognize a ext3/ext4 format.  And he's going to need the cross compatibility until I have him fully converted.

So, question still remains, is there a piece of software that will do automatic copies, or ghosts, or whatever of a hard drive's data to another hard drive, or should I steer this guy toward a more hardware related solution?

---

### Post by psusi on 2011-04-06
Stay away from automatic all together.  What you want is a manual backup to a removable hard disk that you then unplug and store somewhere safe, like a fire proof vault.

I recommend getting an eSATA dock so you can take the drive out of your fire proof safe, drop it in, back up, unplug, and put it back.

I suggest using rsync or a gui frontend like grsync.

---

### Post by ronparent on 2011-04-06
+1 on psusi's recommendations.

I use a MB raid0 (pdc) for speed but have come to a conclusion that a raid1 or any level of raid was too convoluted and an inadvised overkill for a home setup. I do use an external drive (which I keep in a fire safe) as well as network backups on three other computer for irreplaceable pictures. Am also considering 40 or 50Gb of cloud storage.

I have had problems with an Asus board and currently use a Gigabyte. But there is some small chance of failure for even the best hardware and I consider any of the current commercial offerings roughly equivalent and differing more in features and ease of use than relyability.

psusi's comment
> I recommend getting an eSATA dock so you can take the drive out of your fire proof safe, drop it in, back up, unplug, and put it back.
I would also consider an nas network drive (non raid) in a very secure location. 

Good luck. Post if you need any other thoughts.

---

### Post by MiniVanMan on 2011-04-06
I appreciate the help.  You've pretty much just convinced me to go in a direction I was leaning to already.  It helps to get more opinions when trying to convince somebody to go a direction different than what they're "cousin" said.  

I've ran RAID 10 and a few mirrors in the past, but really haven't been happy with them.  With organization and a good backup plan of your critical files, hard drive failure is much less of a concern.  

I find myself repeatedly in the position of trying to create fail safes for unorganized computer users that have become entirely too dependent on one piece of hardware.  Always to the tune of "but that's too complicated, isn't there something that will do it for me?".  Pound head on the desk, and drive on trying to see if there's something latest and greatest out there that will organize unorganized people.

When dealing with 400GB of pictures, and the (I'll call him client, though he's a friend) client can't give you a single "irreplaceable" picture it's hard.  "They're ALL irreplaceable".  No, that just means you threw them on your computer and haven't sorted through them to get rid of even the junk.

---

