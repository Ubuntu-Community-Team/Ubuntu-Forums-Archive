---
title: "Need Help! MADE HUGE Mistake.  I seek wisdom..."
date: 2010-02-02
forum: General Help
---

### Post by demonet on 2010-02-02
First off this is general computer help--involving ubuntu Linux--nothing that is ubuntu's fault or a misunderstanding with Linux. But since I generally enjoy the wisdom of the people here when I seek answers on other things, I decided to post on this forum..

OK....I am running Karmic.  I am using a laptop, but that is only in name, as it sports countless USBs and a second monitor. The main HD has two partitions, Windows 7 and Ubuntu.  I am currently in ubuntu.

In addition, I have a 1TB external drive connected to this laptop which has two partitions.  One is for NTFS (about 700GB), and the other is EXT3 (the remaining amount).

I had a 4gb USB drive plugged in (I have independently powered USB expansions---way too many).  And I got it confused (I do not know how!!) with my ultra-sacred, all-important, my-life-is-over-if-its-lost 1TB external drive. 

I did the following to the external drive [I][B]thinking it was my 4GB pen drive. (!)
[/B][/I]
First, I formatted the first 1.5GB of it as vfat.
Next, I formatted the remainder as EXT3 (so, I guess that would mean that ~995+GB was reformatted from a combination NTFS/EXT3 to EXT3.

Then because I ran into an error trying to copy files to this "pendrive" (which was not the pendrive but my 1TB EXTERNAL drive), being lulled into complacency already having used /dev/sdb/ and not thinking about it when I formatted it, I proceeded to wipe the first 4GB of the drive using dcfldd (using random).  I only stopped at just over 4GB, because that is when my actual intelligence decided to start working as I realized that a 4GB pen drive would not show more than 4000MB during a dd wipe.

I am so panicked, I can barely type this.  Right now, for lack of something to do, I started Testdisk, and am just scanning this drive, which will take another 2 hours or so.

I realize that things can be unformatted (in certain circumstances), but because I destroyed the partition table with dd when I wiped the first 4GB, I am particularly freaked out.

This 1TB drive had everything I own on it and was effectively "secondary storage", except I ended up deleting primary storage for usability.  

In all reality, though this 1TB drive was purchased as a "backup", I only needed to use about 200GB of it as a backup to my bootable normal working HD in my laptop, so I put all of my very valuebale archived files on this external drive, removing them from a collection of other hard drives which were getting two numerous.  As such, I really should have been backing up my external drive, but never thought it would fail, and I was too stupid to foresee a blunder on my part would ever happen.

Anyone out there who can suggest tips, tricks, hacks, or spells..... I would be incredibly grateful..   Going to chain smoke and pace.  I may even become religious.

Paul

---

### Post by Tahakki on 2010-02-02
What did you use to format the drive?

---

### Post by demonet on 2010-02-02
mkfs.vfat and mkfs.ext3 respectively.

---

### Post by jamesisin on 2010-02-02
One recommendation at this point would be to make a disc image so that you have a current snap shot.  Not a fool-proof thing, but it could be useful if something goes wrong as you try to recover the contents.

---

### Post by nothingspecial on 2010-02-02
Do not write anything to the drive until you have exhausted all possibilities.

---

### Post by demonet on 2010-02-02
SO I would need to go get another 1TB drive and then what would I do..> I kow in windows they have norton ghost (which I have never used) but how do I make an image in Linux.... 

And if testdisk works and finds my files, then I would have to copy them (which will be about 500GB to be conservative), I then would need to copy these to another drive. with such a capacity, correct.

So bottom line: to to anything with any reasonable hope for success I am going to need 1.5 to 2TB additional storage.  Which I don't have at this moment... WIll have to wait until tomorrow prob.. 

But is Testdisk what you would recommend? any other utilities?  Unfortauntely, it is primarily the NTFS files that are of most value since they are a stockpile of things from my pre-Linux days.

---

### Post by jamesisin on 2010-02-02
I am trying to recover a borked partition:

[http://ubuntuforums.org/showthread.php?t=1396158](http://ubuntuforums.org/showthread.php?t=1396158)

I created an image using testdisk but haven't figured out how to make that image useful as yet.

---

### Post by nothingspecial on 2010-02-02
There is [[COLOR="Magenta"]photorec[/COLOR]]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by demonet on 2010-02-02
> **nothingspecial said:**
> Linux assumes you know exactly what your doing.

I believe that is part of your signature.  Either way it is a an ominous quote... it is an aspect of Linux that is precisely what drew me to it.  I just have never been so stupid and absent-minded before.

---

### Post by nothingspecial on 2010-02-02
> **demonet said:**
> I believe that is part of your signature.  Either way it is a an ominous quote... it is an aspect of Linux that is precisely what drew me to it.  I just have never been so stupid and absent-minded before.

Yes it is part of my signature, and you`ve got the intent right.

It is supposed to convey the fact that if you ask linux to do something, it will do it. It won`t ask you if you`re sure - just ok done.

I`d love to know where I read it.

I found out the hard way just like you. My backup drives aren`t plugged in and are out of the way in places burgalars would (hopefully) not look.

In fact my friend and I were talking about remote weekly backups to drives located in each others houses the other day.

I may sound paranoid to some, but I bet I don`t to you.

I hope you manage to recover your stuff. I know from experience that your position is not a nice position to be in.

---

### Post by Vaphell on 2010-02-02
regardless of the results, you should rethink your design - one external hdd holding all your precious data accumulated over the years is too little. It's a single, very vulnerable point of failure. You formatted it yourself, but damage could be done by simple hardware malfunction.
Personally i don't bother because i don't consider my stuff to be irreplaceable, but if i had anything like that - be it a complete photo collection from the last 20 years, or a stuff for the master's degree etc - i'd have a backup.

---

### Post by demonet on 2010-02-02
> **Vaphell said:**
> regardless of the results, you should rethink your design - one external hdd holding all your precious data accumulated over the years is too little. It's a single, very vulnerable point of failure. You formatted it yourself, but damage could be done by simple hardware malfunction.
Personally i don't bother because i don't consider my stuff to be irreplaceable, but if i had anything like that - be it a complete photo collection from the last 20 years, or a stuff for the master's degree etc - i'd have a backup.

Trust me, besides having near panic attacks at this moment, I am thinking of anything I can do in the future....  But at the moment, being as though I feel I have one chance to do this RIGHT.  I am trying to ascertain what I need.

I would think the suggestion of making an image first would be prudent.  

Then use testdisk/photorec.  But, given what I have described, in using testdisk (let's just start with that utility since it is already 75% through scanning this drive) would I opt to rewrite the MBR? Again, it is the NTFS parition (80% of the drive) of which I am concerned.  And if the files and files and file structure show up after this scan, then I can just copy them to another Hard drive... correct?

I know this is foolish to even ask, but is it possible perhaps to just restore the MBR on that drive -- since the the formatting is really not all the destructive (therefore it can be undone), since the first 4GB of this 1000GB drive (which were wiped) contain, in a large part,  the data that will enable me to access the entire drive (+ or - a few gigs of files that were part of that 4GB I wiped).  Or would that be too naive to presume possible?

---

### Post by jamesisin on 2010-02-02
Well, there is also the file table which I think is going to be in that first 4GB section.  If so, you'll end up having to seek out individual files (and perhaps without names).

---

### Post by demonet on 2010-02-02
> **jamesisin said:**
> Well, there is also the file table which I think is going to be in that first 4GB section.  If so, you'll end up having to seek out individual files (and perhaps without names).

Yes, I think I know what you mean.  I really don't know what to do.  Besides all of the older valuable data, I had about 150 GB of currently active and necessary data as well.  

If it came down to files without names, I almost think it would be better to save this hard drive and start over with a new one, and start trying to rebuild the data I need for current projects.... because I think trying to figure out the names to various files (.rar, .msi, .psd files. .mov files, .pdf files), it would take me 3 weeks to get these even halfway identified and reorganized.  

My first testdisk scan did not even show the NTFS partition, only the Linux partition (what once was sdb2), so I am running the deeper scan. I hope to god this works. I cannot be set back this much time....!  I know it is my fault, and beating myself up is not helping at the moment in achieving the overall objective. But I really have not felt this stressed in as long as I can remember.

---

### Post by jamesisin on 2010-02-02
Check out the thread link I posted above.  I have been trying to recover a client's drive and it's not going so well.

Not that I want to bring you down, but you might find useful information in there.

Of course, suggestions are always welcome.

---

### Post by demonet on 2010-02-02
I have read it, and am keeping an eye on it, but as thee are some differences, I am too unsure as to what I need to do..

For instance.

this is what fdisk -l looked like when it was fine, before my idiocy....

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       93062   747520483+   7  HPFS/NTFS
/dev/sdb2           93063      121601   229239517+  83  Linux

```

But then after testdisk's first scan, it shows the following.

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121602 255 63


I see that the ending cylinder in testdisk matches the ending cylinder in the fdisk above, but  that just means  -- for the moment let's hope anyway -- that testdisk just sees that partition, and that partition ends at cylinder 121602?  So there is no real benefit yet...

And although in your thread, you are writing MBRs per Testdisk's scans, are you working of an image, or the original?  Either way doing so doesn't seem to be of too much benefit in your recovery efforts.

Lastly,  I was wondering if Photorec (or any other tool) would in these circumstances be a wiser move.  Any suggestions?

---

### Post by jamesisin on 2010-02-02
Yeah, in my situation I am dealing with a boot drive so makes sense to look at the MBR.  Changing the MBR has only seemed to confirm that it's a partition table problem.

Though in fairness those applications that were able to read the table before testdisk are those able to read it after (and those not able before are still not able), so I don't see that I have made any progress (except perhaps knowledge).

I don't know anything about Photorec except that it has a good reputation.  Unfortunately it's limited to photo-style files (not things like .doc or .conf or .whatever).

---

### Post by mdrake36 on 2010-02-02
I just gravitate to this kinda stuff.
I am a real novice but just on the surface I know that while you originally partition your drive during install it tells you you can undue the table later.
I wonder what program gives the ability during install steps to undue a partition table?
Hope I don't make it worse dude.
Good luck:popcorn:

---

### Post by demonet on 2010-02-02
Doesn't ext3 have some sort of ability given how the filesystem is set up with superblock backups, etc. to allow me to undo any of the 4GB that were wiped? 

I am guessing that this may only apply to files that are deleted and not when you wipe  some portion of the drive.

I thought I would ask just the same.  Still waiting on my second "deep scan" with Testdisk.  

As far as Photorec and Testdisk, I think they have similar recovery abilities, but I am not sure.  I read the description for both and it seems that Photorec can manage file extensions better.  But that may have just been my interpretation. 

I am so screwed.  I was going to go online with a website in the next 3 or 4 days, and 90% of the files needed for it were on that drive... it was my first DIY home hosted web server, and it had taken me months to learn enough PHP and javascript to make the pages professional.  

Plus all of the instructional videos I had (in PHP, JS, Perl, Python, Flash, ASP)--only copy I had were on that drive.  That was at least $15,000 of irreplaceable data.

I am sick. I don't even want to be in the same room as my PC.  My brain is voting for believing it never happened.

---

### Post by demonet on 2010-02-02
[EDIT] DELETED

See next post....

Paul

---

### Post by demonet on 2010-02-02
Only 80% through the deep-scan, but at least the partition is showing up:

```
  HPFS - NTFS              0   1  8 82862 254 63 1331194025
  Linux                82863   0  1 121600 254 61  622325968 [Linux_Backup]
  Linux                82863   0  1 121600 254 61  622325968 [Linux_Backup]
  HPFS - NTFS              0   1 15 93061 254 63 1495040953
  Linux                93062   0  1 121600 254 60  458479032 [Linux_Backup]
  Linux                93062   0  1 121600 254 60  458479032 [Linux_Backup]
```Don't know quite what that all means, except the NTFS partition was cylinders 1 through 93062, so it is being found... To what degree.... that remains to be seen.

Can anyone explain to me what this is showing me (have always been very bad at disk geometry).  But the C-H-S info on the two HPFS-NTFS lines is different, and I was wondering why.  The number of sectors, specifically, is different... is this just a function of the progress Testdisk is making??

Paul

---

### Post by demonet on 2010-02-02
OK... I am not asking to be spoon fed anything, but this was the output of Testdisk after the "deep scan".  I do not want to be presumptuous, but the last line makes me think there might be good news in all of this...

```
Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121602 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1 121600 254 63 1953520002
D HPFS - NTFS              0   1  8 82862 254 63 1331194025
D HPFS - NTFS              0   1 15 93061 254 63 1495040953
D Linux                82863   0  1 121600 254 63  622325970 [Linux_Backup]
D Linux                93062   0  1 121600 254 63  458479035 [Linux_Backup]




Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS found using backup sector!, 1000 GB / 931 GiB

```

Can someone tell me what this means? What is a "backup sector"?

And should I still create an image of this drive?  Advice at this point would be quite appreciated.  I feel encouraged by this output--I hope this is positive.  ;)

Paul

---

### Post by jamesisin on 2010-02-03
It's nice to feel encouraged.  Even when it turns out to be bunk.

I would still make an image if you are able.  You will want to make a partition image(s) where possible (because they are supposedly easier to use than disk images).

---

### Post by t4thfavor on 2010-02-03
Looks like it found em, also looks like a program I have never used. Do the image, and then start messing with it.

You can use ddrescue to make copies from disk to disk and it's easier than dd.

Then try recovering it, if you mess it up you just have to ddrescue it in reverse and try again.

Good luck,

RAID, and multiple offsite backups are king.

---

### Post by bakegoodz on 2010-02-03
Realistically you can recover, if your lucky some stuff. Photorec can scan every bit of the drive and find stuff by file type, not going to see the old filenames any more. Some photos and such will be missing parts too.

---

### Post by demonet on 2010-02-03
> **bakegoodz said:**
> Realistically you can recover, if your lucky some stuff. Photorec can scan every bit of the drive and find stuff by file type, not going to see the old filenames any more. Some photos and such will be missing parts too.

So far this seems to be the case.  I am not going to give up though and am going to hope that there is some tool, method or combination of same that might yied better results than 50,000-100,000 files with seemingly random lettered/numbered names (I realize they are not random and have to do with their file allocation).

In order to pursue this goal, I have purchased three additional One (1) Terabyte external drives.  I need to make an image first.  I do not see how this is done in testdisk or Photorec.  If someone could assist me with this, I would be grateful.

Secondly, once I have the image copied, I want to run ddrescue.  I have read the documentation, however, if there is anyone who has used ddrescue (the GNU version), if they had any suggestions givien my circumstances, again, I would be grateful.

Lastly, if the above fails or falls short, I am going to try and run some windows apps as  the partition that I need to recover--that is more valuable than its weight in platinum to me -- is NTFS, so while I instinctively trust Linux, I am going to roll the dice and see if some software or some company can recover this for me, even if it costs $1000.  However, I need to know what I can do with getting windows to recognize this drive since I cannot mount it as I do in Linux.  Do I need to have testdisk/photorec write an MBR?  

I need this data.

Sincere thanks to anyone who can provide any information which will lead me to this goal.

Paul

---

### Post by jamesisin on 2010-02-03
After you have scanned in testdisk, you will get an option to create images.

---

### Post by demonet on 2010-02-03
Well I did that, but then since Photorec was recommend, I switched after the scan was complete--because Photorec seemed to use the data that Testdisk used/generated.  I don't want to waste another 5 hours using Testdisk to scan it, just becasue it has this feature.

 I wish I had known that Testdisk was the only application that can write an image.

Does anyone know if photorec can write an image file???

Thanks!

---

### Post by rahilm on 2010-02-03
i hope that u recover everything.
this experience will make you careful everytime you mess with partitions. i had a similar experience but i recovered everything thanks to testdisk's scan which recovered my partition table.
[[[Always make a sanity check]]]

---

### Post by rahilm on 2010-02-03
clonezilla becomes a great help in such situations..

---

### Post by paxxus on 2010-02-03
I recently made a 1:1 copy of my main drive using dd:

```

> sudo -s
> dd if=/dev/sdx of=/dev/sdy &
> pid=$!
> while kill -USR1 $pid; do sleep 1; done
```The two lines after the dd command itself is just some woodoo to be able to see the progress. None of the drives should be mounted.

In the above example the source disk ("input file") is sdx and the target disk ("output file") is sdy. Obviously you want to get this right.

There are probably some more user-friendly ways of copying all bits on the drive though :)

---

### Post by demonet on 2010-02-03
> **paxxus said:**
> I recently made a 1:1 copy of my main drive using dd:

```

> sudo -s
> dd if=/dev/sdx of=/dev/sdy &
> pid=$!
> while kill -USR1 $pid; do sleep 1; done
```The two lines after the dd command itself is just some woodoo to be able to see the progress. None of the drives should be mounted.

In the above example the source disk ("input file") is sdx and the target disk ("output file") is sdy. Obviously you want to get this right.

There are probably some more user-friendly ways of copying all bits on the drive though :)

Thank you... I consider myself an above-average dilettante, but I must admit this is one area I know woefully little.  I am willing to stay up for the next 72 hours to fix this.  This is more serious to me than anything I can imagine.  And yes, I lead a shallow life.

But given that NTFS is a different filesystem with sectors or areas which contain meta-data throughout, I am hoping to find a solution.  Does anyone know ANYTHING about NTFS? Such as a reputable application to recover?  I know I am talking to Linux people here, but I was just hoping for a little more guidance.  

Can anyone recommend a forum dedicated to data recovery?

---

### Post by t4thfavor on 2010-02-03
unmount both drives, and issue

```

sudo ddrescue /broken/drive /new/drive

```
Wait a long time, and it will make a disk to disk copy of the broken disk to the new disk.

You can also supplement that for future reference with 
```

sudo ddrescue /broken/disk /path/to/mydisk.iso

```

---

### Post by hunterkasy on 2010-02-03
> **demonet said:**
> So far this seems to be the case.  I am not going to give up though and am going to hope that there is some tool, method or combination of same that might yied better results than 50,000-100,000 files with seemingly random lettered/numbered names (I realize they are not random and have to do with their file allocation).

In order to pursue this goal, I have purchased three additional One (1) Terabyte external drives.  I need to make an image first.  I do not see how this is done in testdisk or Photorec.  If someone could assist me with this, I would be grateful.

Secondly, once I have the image copied, I want to run ddrescue.  I have read the documentation, however, if there is anyone who has used ddrescue (the GNU version), if they had any suggestions givien my circumstances, again, I would be grateful.

Lastly, if the above fails or falls short, I am going to try and run some windows apps as  the partition that I need to recover--that is more valuable than its weight in platinum to me -- is NTFS, so while I instinctively trust Linux, I am going to roll the dice and see if some software or some company can recover this for me, even if it costs $1000.  However, I need to know what I can do with getting windows to recognize this drive since I cannot mount it as I do in Linux.  Do I need to have testdisk/photorec write an MBR?  

I need this data.

Sincere thanks to anyone who can provide any information which will lead me to this goal.

Paul



If you do end up needing professional help on the data recovery, ontrack is a really good company, this company worked on the hhd for space shuttle Columbia in 2003 but it will cost money, my brother in-law was quoted up to $3,000 for data recovery on a dead hhd drive

[http://www.ontrackdatarecovery.com/minnesota/data-recovery-minnesota.aspx](http://www.ontrackdatarecovery.com/minnesota/data-recovery-minnesota.aspx)

---

