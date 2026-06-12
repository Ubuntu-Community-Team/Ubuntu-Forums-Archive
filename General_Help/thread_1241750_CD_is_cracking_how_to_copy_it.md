---
title: "CD is cracking how to copy it?"
date: 2009-08-16
forum: General Help
---

### Post by OttoMann on 2009-08-16
Hi!

I have an problem with my old game CD. On the inner rim of the "hole in the middle" a crack developed some time ago. Since the CD must be inserted to play the game it rotates and the crack is now spreading toward the outer rim of the CD.

So is there a way to make an accurate ISO of the CD and burn that ISO on a new blank CD witch will be then used instead of the cracked original CD?

I have tried Brasero but I have got transfer rates of around 1 Kb/s so it would take forever to make an ISO. Is this an copy protection issue or is the CD   already beyond repair (it still works when playing the game)?

Any suggestions?

---

### Post by scouser73 on 2009-08-16
Brasero has a function for copying a disc. Brasero can be found in the repos.

---

### Post by Penguin Guy on 2009-08-16
Most games check if the CD is in the drive and then play, they don't actually read data from the CD (other than maybe to verify that it's the correct CD). You can usually download mods for games that will allow you to play them without the CD - maybe you should look into this instead.

---

### Post by OttoMann on 2009-08-16
> **scouser73 said:**
> Brasero has a function for copying a disc. Brasero can be found in the repos.

Hi!

Yes I tried to use Brasero, but when I tried the copy function it was unbelievably slow (around 1 Kb/s reading the disc), so I don't know is this due to disc being cracked and old or is there some copy write protection witch slows down the reading process. 

How copyrighting for Widows programs can work (if at all - most probably not) in Linux is another question.:confused:

---

### Post by OttoMann on 2009-08-16
> **Penguin Guy said:**
> Most games check if the CD is in the drive and then play, they don't actually read data from the CD (other than maybe to verify that it's the correct CD). You can usually download mods for games that will allow you to play them without the CD - maybe you should look into this instead.
Hi!

I guess if I run out of options for making an backup this will remain the only option (and not an entirely legal I guess:rolleyes:).

---

### Post by 4Orbs on 2009-08-16
In my experience it is common to get slow read speeds when copying a game disc to iso. The slow speeds only occur on the few hidden sectors of the gamedisc and regardless of the slow periods the entire disc should succesfully copy in less than one hour (usually). This is assuming that the crack in the disc isn't causing repeated re-try's due to errors.

---

### Post by HavocXphere on 2009-08-16
CDs spin up to quite high speeds in the drive (Thousands of RPMs). I'd advise against putting damaged CDs in a CD drive...it could be dangerous. Even CDs that look 100% sometimes shatter. Plus it is likely to kill the CD drive too.

---

### Post by OttoMann on 2009-08-16
> **4Orbs said:**
> In my experience it is common to get slow read speeds when copying a game disc to iso. The slow speeds only occur on the few hidden sectors of the gamedisc and regardless of the slow periods the entire disc should succesfully copy in less than one hour (usually). This is assuming that the crack in the disc isn't causing repeated re-try's due to errors.

Hi!

I didn't know that. 
Brasero always reported "fantastic" estimated times like several days, so I simply stoped the procedure.

Will try it out now hopefully I will now after an hour or so....:)

---

### Post by HotShotDJ on 2009-08-16
> **OttoMann said:**
> So is there a way to make an accurate ISO of the CD and burn that ISO on a new blank CD witch will be then used instead of the cracked original CD?Try the following script (copy to a text file and then make executable).  You'll need to change the read and write devices.  If you don't have two drives, you'll need to get rid of the "--on-the-fly" switch and make sure that "--source-device" and "--device" both point to the same place.  Although I haven't used this method on game CD's, I have used on other types of discs that have copy protection and "hidden" sub-channel data.  Just for the record, it is not illegal to make a copy of discs that you legally purchased, no matter what the CD publishers would like you to believe.

```
#!/bin/bash
umount /dev/scd0
sudo cdrdao copy --source-device /dev/scd0 --device /dev/scd1 --on-the-fly --driver generic-mmc-raw --read-subchan rw_raw --paranoia-mode 3
sudo -K
```

---

### Post by OttoMann on 2009-08-16
> **HavocXphere said:**
> CDs spin up to quite high speeds in the drive (Thousands of RPMs). I'd advise against putting damaged CDs in a CD drive...it could be dangerous. Even CDs that look 100% sometimes shatter. Plus it is likely to kill the CD drive too.
HI!

I know, I herd horror stories about disc disintegrading in the dives too... this is my main motivation behind making an backup copy...

---

### Post by NickCollide on 2009-08-16
Have you also tried a lens cleaner? Also, what I've been doing lately w/ my cds (assuming your game is on a cd and not a dvd although this should probably work as well) is just putting them into the drive, then kill off any windows that open up, right click the icon for the disk, and select 'copy image' (or whatever comes up) then changing the destination to an .iso image on the harddrive, that way I have both a mountable image for Virtualbox machines, and I can right click that image and select 'write to disk' at a later time. I always thought that was about as 'automagical' as it gets. :)

NC
ps: the reason i noted the difference between cds and dvds is i made a backup of a film dvd that i own, and the resulting file was too big to copy to an external harddrive that i had (which had either the FAT32 or NTFS - can't remember which now) and the filesystem had a 4 gig size limit (the disk was dual layer w/ a nearly 9 gig size)

pps: also, if you go the 'gray legal' area route, you may just find an .iso online that you could download yourself.

ppps: if the game is old enough, but still available, you might just buy a new copy if the price low enough (like $5-$10 or so)
if it's worth playing enough to break it, that might be a viable option as well. :)

---

### Post by OttoMann on 2009-08-16
> **HotShotDJ said:**
> Try the following script (copy to a text file and then make executable).  You'll need to change the read and write devices.  If you don't have two drives, you'll need to get rid of the "--on-the-fly" switch and make sure that "--source-device" and "--device" both point to the same place.  Although I haven't used this method on game CD's, I have used on other types of discs that have copy protection and "hidden" sub-channel data.  Just for the record, it is not illegal to make a copy of discs that you legally purchased, no matter what the CD publishers would like you to believe.

```
#!/bin/bash
umount /dev/scd0
sudo cdrdao copy --source-device /dev/scd0 --device /dev/scd1 --on-the-fly --driver generic-mmc-raw --read-subchan rw_raw --paranoia-mode 3
sudo -K
```

Hi!

Thank you for your script sample as I am quite new to Linux and command line is still very new  to me.

Currently I am trying out 4Orbs's "recipe" and have to wait for only 118:36:24 hours (hopefully not), if it fails I will use your script.

---

### Post by 4Orbs on 2009-08-16
> wait for only 118:36:24 hours
I have had to wait no longer than 2 hours, ever. Don't be discouraged yet (if you pass the 2 hour mark, then be discouraged but still wait a while more). A cheerful sidenote: copying a game cd on Windows XP, using Alcohol will give those same multi-day estimates for completion.

---

### Post by OttoMann on 2009-08-16
> **NickCollide said:**
> Have you also tried a lens cleaner? Also, what I've been doing lately w/ my cds (assuming your game is on a cd and not a dvd although this should probably work as well) is just putting them into the drive, then kill off any windows that open up, right click the icon for the disk, and select 'copy image' (or whatever comes up) then changing the destination to an .iso image on the harddrive, that way I have both a mountable image for Virtualbox machines, and I can right click that image and select 'write to disk' at a later time. I always thought that was about as 'automagical' as it gets. :)

NC
ps: the reason i noted the difference between cds and dvds is i made a backup of a film dvd that i own, and the resulting file was too big to copy to an external harddrive that i had (which had either the FAT32 or NTFS - can't remember which now) and the filesystem had a 4 gig size limit (the disk was dual layer w/ a nearly 9 gig size)

pps: also, if you go the 'gray legal' area route, you may just find an .iso online that you could download yourself.

ppps: if the game is old enough, but still available, you might just buy a new copy if the price low enough (like $5-$10 or so)
if it's worth playing enough to break it, that might be a viable option as well. :)

HI!

Didn't try the lens cleaner but I did clean the CD with some wipes for Cd's.

As for the copying procedure I do the same, unnecessary programs just bog down my aging laptop (1,6 Ghz Celeron).

I think the 4 Gb limit is an fat32 "feature".

The "gray legal" options I am fully aware of, but I would like to stay on "withe legal":) side of the Torrent.

I already bought the game reduced because it was old in 2002 already.

---

### Post by OttoMann on 2009-08-16
> **4Orbs said:**
> I have had to wait no longer than 2 hours, ever. Don't be discouraged yet (if you pass the 2 hour mark, then be discouraged but still wait a while more). A cheerful sidenote: copying a game cd on Windows XP, using Alcohol will give those same multi-day estimates for completion.

Hi!

I am now waiting for 35 minutes and estimate is at 388:45:59, so I hope you are right....

---

### Post by AmerNewbieInDE on 2009-08-16
is the cd totally cracked through? i mean including the inner film? with the time showing, sounds like it is having alot of rereading to do and in the end, it will tell you sorry, but there were errors... or, with it spinning so long, you take a chance of that disk heating up too much and shatering... reason that you can still play the game is probably the sector the program looks for is in a good area of the disk.. have you tried to contact the company that made it for a replacement?

oh, if it hasnt ripped the film, (this might also eat away the cd) try a very little superglue on the inner radius of the disk, nothing in the data area and nothing on the label side... you might be stabilize the crack enough.

---

### Post by 4Orbs on 2009-08-16
You know I can't guarantee anything. But when it comes to copying a game to iso... don't trust those estimates. They are based on the current (slow) read speed as applied to the file size of the entire cd. The actual hidden sectors of the cd are relatively small, but at the slow read speed they make up the bulk of the time consumed in the copy process. If your disc is still playable without errors, then you should end up with a successful copy.

---

### Post by OttoMann on 2009-08-16
> **AmerNewbieInDE said:**
> is the cd totally cracked through? i mean including the inner film? with the time showing, sounds like it is having alot of rereading to do and in the end, it will tell you sorry, but there were errors... or, with it spinning so long, you take a chance of that disk heating up too much and shatering... reason that you can still play the game is probably the sector the program looks for is in a good area of the disk.. have you tried to contact the company that made it for a replacement?

oh, if it hasnt ripped the film, (this might also eat away the cd) try a very little superglue on the inner radius of the disk, nothing in the data area and nothing on the label side... you might be stabilize the crack enough.

Hi!

It is well cracked alright it goes from the inside to/through the silver aluminum film and the tip of the crack ist just touching the data area on the disc. 

The super glue is a good idea (hopefully I won't glue the disc to my fingers..)

---

### Post by OttoMann on 2009-08-16
> **4Orbs said:**
> You know I can't guarantee anything. But when it comes to copying a game to iso... don't trust those estimates. They are based on the current (slow) read speed as applied to the file size of the entire cd. The actual hidden sectors of the cd are relatively small, but at the slow read speed they make up the bulk of the time consumed in the copy process. If your disc is still playable without errors, then you should end up with a successful copy.
Hi!

I know, I know... I am just an impatient type so when ever I saw 100+ hours I canceled the process.

Right now I am waiting it out and keeping my fingers crossed (makes typing very difficult...).

---

### Post by 4Orbs on 2009-08-16
I'll bet those estimated long waits prevent lots of people from ever trying to play their game with an iso copy mounted on a virtual drive.

---

### Post by AmerNewbieInDE on 2009-08-16
if you do use the super glue, remember, only as last try, and not too much to mess with the balance. if the film and the label are ok, then it might take awhile, as you have seen, but should be able to get all off

---

### Post by Post Monkeh on 2009-08-16
first thing i would do is back up the cd itself in case you ever need to reinstall the game.

then worry about backing it up in a way that will allow you to keep playing the game without a no-cd crack.

---

### Post by OttoMann on 2009-08-17
Hi!

Problem SOLVED!

After leaving Brasero work on the disc for the whole night and still shoving some 600 hours estimated time to go I quit the procedure.

A friend of mine thought that CD drives in notebooks are not as accurate as desktop components, so I dusted of my old PC, borrowed my friends CD-R unit, downloaded Alcohol and in 2:54 the nightmare was over!

Now I have a an working CD backup and the crack on the original is partially fixed with super glue.

Thank you all for quick and extensive help in such minor trouble.

P.S.
 It just came to me This is another case of problems solved by alcohol! :D:D

---

### Post by Post Monkeh on 2009-08-19
alcohol. the cause of, and solution to, all of life's problems © Homer Simpson

---

