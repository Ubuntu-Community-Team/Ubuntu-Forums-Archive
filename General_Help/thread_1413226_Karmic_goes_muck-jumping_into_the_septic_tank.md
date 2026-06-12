---
title: "Karmic goes muck-jumping into the septic tank"
date: 2010-02-22
forum: General Help
---

### Post by Gnusboy on 2010-02-22
Been using [U]Ubuntu Karmic 9.10 for a few months- but now it has a mind of its own.
[/U]About a week ago, Firefox would crash for no apparent reason. Then it became an increasing event. Today, after using the machine normally for several hours, it started crashing Firefox and Yelp before they loaded completely. It crashed again and again until it finally froze,
I had to do a hard reboot and then it would not load properly and then crash.
I checked the event logs and saw some warnings about an ALSA bug_ and then more _as it deteriorated.
Now it seems to boot but then when the Ubuntu logo shows up all it does is flash for a few minutes and then the screen goes black and the system freezes.
I tried using the recovery disk, but after 1 1/2 hours of black screen it reported
HD Error 0
and 6 Bus errors
And finally ended with invalid user "Ubuntu"

Then I put in a fresh copy of Karmic and ran it in recovery mode. It didn't recover and from the machine I then tried a live CD and it booted to the black screen and froze
And after I tried to do a new install I am getting lines and lines of errors like this
[ 1047 .871988] SQUASHFS error: Unable to read data cache entry [27f21194]
And about 1000 more similar.
I ran a disc integrity check which found errors,
I was going to just do a re-install, but when it started it froze and that's whats been happening.
I don't know what to do at this poit because All I can think about is the data I will lose if I have to slick the drive 
AGAIN to get this sucker working.
Any advice will be appreciated.

---

### Post by NCLI on 2010-02-22
To me, it sounds like something is very wrong with your HDD or filesystem.

Anyway, what I would do is boot it from a Live CD and use some kind of external/online storage to backup your important data, then try reinstalling. If that fails, you'll need to buy a new HDD.

---

### Post by sdowney717 on 2010-02-22
sounds like a hard disk error. And maybe ram issues
when you get it going again, use firefox 3.6 or chrome. i have not had any lockups with those browser versions. firefox 3.5 would give me lockups.

get a new drive install ubuntu, then copy the data from the problem drive over.

---

### Post by Gnusboy on 2010-02-22
I ran a drive integrity check and it passed and it passed an over night memtest.
The drive is about 6 months old.
I've tried the recovery in the current several times,but it goes to a black screen with a white dot in the center which spins, but does nothing else. It also freeze the system and I have to do a hard boot  to release it.
Can I re-install ANY version of Ubuntu to save the data? Or is it right back to a total install and a data overwrite?
This is the 3rd time this has happened in 6 months.
Going back to WinBlows is looking better every time.
Please guys - help me fix this problem.

PS There have been 3 versions of Karmic listed 9.10.14 , 9.10.17 , and 9.10.19 which is also listed as beta.
Does this have relevance?
I tried rolling back the kernals, but it didn't work.

If I do a re-install of Karmic or Jaunty does it automatically overwrite the data on the drive? 
I'm at the section where it wants to partition the drives - #1 Primary 318.2 GB B  EXT4, #6 logical 299.1GB  EXT4
#7 logical 11.4GB F Swap swap
#5 logical 11.4GB F swap swap

Do I have a save here, or can I simply skip the partitioning and reload a kernal?
All help appreciated.
Thanks

---

### Post by Gnusboy on 2010-02-23
**Karmic goes muck-jumping into the septic tank** 			
 			 			 		   		 		 		Been using [U]Ubuntu Karmic 9.10 for a few months- but now it has a mind of its own.
[/U]About a week ago, Firefox would crash for no apparent reason. Then it became an increasing event. Today, after using the machine normally for several hours, it started crashing Firefox and Yelp before they loaded completely. It crashed again and again until it finally froze,
I had to do a hard reboot and then it would not load properly and then crash.
I checked the event logs and saw some warnings about an ALSA bug_ and then more _as it deteriorated.
Now it seems to boot but then when the Ubuntu logo shows up all it does is flash for a few minutes and then the screen goes black and the system freezes.
I tried using the recovery disk, but after 1 1/2 hours of black screen it reported
HD Error 0
and 6 Bus errors
And finally ended with invalid user "Ubuntu"

Then I put in a fresh copy of Karmic and ran it in recovery mode. It didn't recover and from the machine I then tried a live CD and it booted to the black screen and froze
And after I tried to do a new install I am getting lines and lines of errors like this
[ 1047 .871988] SQUASHFS error: Unable to read data cache entry [27f21194]
And about 1000 more similar.

I was going to just do a re-install, but when it started it froze and that's whats been happening.


I ran a drive integrity check and it passed and it passed an over night memtest.
The drive is about 6 months old.
I've tried the recovery in the current several times,but it goes to a black screen with a white dot in the center which spins, but does nothing else. It also freeze the system and I have to do a hard boot to release it.

Can I re-install ANY version of Ubuntu to save the data? Or is it right back to a total install and a data overwrite?

This is the 3rd time this has happened in 6 months.
Please guys - help me fix this problem.

PS 
There have been 3 versions of Karmic listed 9.10.14 , 9.10.17 , and 9.10.19 which is also listed as beta.
Does this have relevance?
I tried rolling back the kernals, but it didn't work.

If I do a re-install of Karmic or Jaunty does it automatically overwrite the data on the drive? 
I'm at the section where it wants to partition the drives
 - #1 Primary 318.2 GB B  EXT4, #6 logical 299.1GB  EXT4
#7 logical 11.4GB F Swap swap
#5 logical 11.4GB F swap swap

Do I have a save here, or can I simply skip the partitioning and reload a kernal?
All help appreciated.
Thanks

---

