---
title: "Storage Suggestions"
date: 2010-12-06
forum: General Help
---

### Post by KillerSiafu on 2010-12-06
My MediaCenter that I built a few years ago has been running a four-drive, software RAID-5 array up until this week. I believe I may have degraded the array to the point where it's not recoverable. There's more info on that [**here**]("http://www.linuxforums.org/forum/ubuntu-linux/172617-raid-5-problem.html") if you think you might be able to help, it would be much appreciated!

However, I'm starting to come to terms with the fact that I probably will not be able to save the array. If that is indeed the case, I need to make a decision as to how I should handle my storage needs going forward.

I currently have:

[LIST]
[*]1x - 160GB WD Internal HD (for the Operating System and software)
[*]4x - 500GB WD Internal Hard Drive (for data storage - previously made up the array)
[*]1x - 1TB WD Hard Drive in an External Dock (hot swap)
[/LIST]

So I'm trying to figure out what the best storage configuration would be. Obviously I'll be keeping the 160GB internal drive for my operating system, software, local documents, etc.

Before this whole disaster with my RAID array, I had the four internal 500GB drives setup in a software RAID-5 array and was using the external 1TB drive as backup / overflow for my array, which was pretty full.

As I see it, if I'm unable to recover the array, I'll have to format and repartition the four 500GB drives and then either:

[LIST=1]
[*]Create a new RAID array
[*]Use them as individual storage drives
[/LIST]

If I create a new array:

**Pros**: 
[LIST]
[*]The four drives are treated as one mounted volume (making organization easier)
[*]There is redundancy should a drive fail (although that doesn't always work!)
[/LIST]

**Cons:**
[LIST]
[*]It's more complex than leaving the drives be stand-alone
[*]There is a risk of losing everything if a drive fails (as I just learned)
[*]I lose one of the drives storage capacity to redundancy
[/LIST]

If I use the four drives as stand-alone storage drives:

**Pros:**
[LIST]
[*]It's much simpler to implement
[*]The loss of one drive doesn't put all of my data at risk
[*]I get the full storage capacity of all four drives
[*]Would most likely see a slight performance increase (read/write)
[/LIST]

**Cons:**
[LIST]
[*]Splitting up / organizing the data across four drives is more work and much more tedious than dealing with one large volume
[*]One drive failing guarantees the loss of data on that drive
[/LIST]

Anyone have any suggestions / arguments as to which makes the most sense? Is there another option to consider?

---

### Post by lrgmmc on 2010-12-06
how is your media organized now?

---

### Post by DeMus on 2010-12-06
> **KillerSiafu said:**
> My MediaCenter that I built a few years ago has been running a four-drive, software RAID-5 array up until this week. I believe I may have degraded the array to the point where it's not recoverable. There's more info on that [**here**]("http://www.linuxforums.org/forum/ubuntu-linux/172617-raid-5-problem.html") if you think you might be able to help, it would be much appreciated!

However, I'm starting to come to terms with the fact that I probably will not be able to save the array. If that is indeed the case, I need to make a decision as to how I should handle my storage needs going forward.

I currently have:

[LIST]
[*]1x - 160GB WD Internal HD (for the Operating System and software)
[*]4x - 500GB WD Internal Hard Drive (for data storage - previously made up the array)
[*]1x - 1TB WD Hard Drive in an External Dock (hot swap)
[/LIST]

So I'm trying to figure out what the best storage configuration would be. Obviously I'll be keeping the 160GB internal drive for my operating system, software, local documents, etc.

Before this whole disaster with my RAID array, I had the four internal 500GB drives setup in a software RAID-5 array and was using the external 1TB drive as backup / overflow for my array, which was pretty full.

As I see it, if I'm unable to recover the array, I'll have to format and repartition the four 500GB drives and then either:

[LIST=1]
[*]Create a new RAID array
[*]Use them as individual storage drives
[/LIST]

If I create a new array:

**Pros**: 
[LIST]
[*]The four drives are treated as one mounted volume (making organization easier)
[*]There is redundancy should a drive fail (although that doesn't always work!)
[/LIST]

**Cons:**
[LIST]
[*]It's more complex than leaving the drives be stand-alone
[*]There is a risk of losing everything if a drive fails (as I just learned)
[*]I lose one of the drives storage capacity to redundancy
[/LIST]

If I use the four drives as stand-alone storage drives:

**Pros:**
[LIST]
[*]It's much simpler to implement
[*]The loss of one drive doesn't put all of my data at risk
[*]I get the full storage capacity of all four drives
[*]Would most likely see a slight performance increase (read/write)
[/LIST]

**Cons:**
[LIST]
[*]Splitting up / organizing the data across four drives is more work and much more tedious than dealing with one large volume
[*]One drive failing guarantees the loss of data on that drive
[/LIST]

Anyone have any suggestions / arguments as to which makes the most sense? Is there another option to consider?

If you go for a safe system you could also try this:
2 disks in a raid 0 configuration ( 2*500GB = 1TB )
2 disks in a raid 0 configuration ( 2*500GB = 1TB )
Place the two raid 0 configurations in a raid 1 ( 1TB // 1TB = 1TB )

Pro: it gives you double speed for reading and writing ( raid 0 ) and it gives the safety from a mirror disk ( raid 1 )
Con: from 2TB in total you only keep 1TB, the rest is redundant

A raid 5 configuration has a complex way of getting your data restored after a crash and, as you also wrote, this does not always work.
A raid 1 has the advantage of saving everything to 2 parallel disks, so if one crashes, the other one still has all the data. It is much easier to restore.
A raid 0 has no redundancy and only gives you extra speed by writing and reading from 2 disks at the same time, each holding half of the data.

---

### Post by KillerSiafu on 2010-12-06
The media box uses XBMC as its front end. My three large media sections are my Movies, TV Episodes, and Music; which each have their own folder and are organized as follows:

Movies (folder)
--> Movie Title (folder)
----> Movie File
----> nfo file
----> artwork files

TV (folder)
--> TV Show Title (folder)
----> Season X (folder)
-------> Episode Files
-------> Episode nfo files
-------> Episode artwork files

Music (folder)
--> Genre (folder)
----> Artist (folder)
------> Album (folder)
---------> Song files

---

### Post by KillerSiafu on 2010-12-06
> **DeMus said:**
> If you go for a safe system you could also try this:
2 disks in a raid 0 configuration ( 2*500GB = 1TB )
2 disks in a raid 0 configuration ( 2*500GB = 1TB )
Place the two raid 0 configurations in a raid 1 ( 1TB // 1TB = 1TB )

Pro: it gives you double speed for reading and writing ( raid 0 ) and it gives the safety from a mirror disk ( raid 1 )
Con: from 2TB in total you only keep 1TB, the rest is redundant

A raid 5 configuration has a complex way of getting your data restored after a crash and, as you also wrote, this does not always work.
A raid 1 has the advantage of saving everything to 2 parallel disks, so if one crashes, the other one still has all the data. It is much easier to restore.
A raid 0 has no redundancy and only gives you extra speed by writing and reading from 2 disks at the same time, each holding half of the data.

Hm that's an interesting idea. I'm not wild about losing two drives to redundancy (especially since I was basically full at 1.5TBs before)... but if I'm starting over anyway, that does seem simpler from a data restoration standpoint.

---

### Post by lrgmmc on 2010-12-06
ok thats really similar to mine.
 
hdd1
------movies
--------0-9
--------a-m
 
 
hdd2
------movies
--------n-z
 
hdd3
------tvshows
--------0-9
--------a-m
 
hdd4
------tvshows
--------n-z
------Music
--------All
 
this way you have plenty of space for each catagory.
then a simple rsync script could backup the data to your 1Tb and or retrive the data ie
 
backup
 
rsync -aW --progress /media/hdd1/ /media/1Tb/
rsync -aW --progress /media/hdd2/ /media/1Tb/
rsync -aW --progress /media/hdd3/ /media/1Tb/
rsync -aW --progress /media/hdd4/ /media/1Tb/
 
restore
 
rsync -aW --progress /media/1Tb/movies/[A-M]* /media/hdd1/movies/
rsync -aW --progress /media/1Tb/movies/[0-9]* /media/hdd1/movies/
rsync -aW --progress /media/1Tb/movies/[N-Z]* /media/hdd2/movies/
rsync -aW --progress /media/1Tb/tvshows/[A-M]* /media/hdd3/tvshows/
rsync -aW --progress /media/1Tb/tvshows/[0-9]* /media/hdd3/tvshows/
rsync -aW --progress /media/1Tb/tvshows/[N-Z]* /media/hdd4/tvshows/
rsync -aW --progress /media/1Tb/music /media/hdd4/music

---

### Post by DeMus on 2010-12-06
> **KillerSiafu said:**
> Hm that's an interesting idea. I'm not wild about losing two drives to redundancy (especially since I was basically full at 1.5TBs before)... but if I'm starting over anyway, that does seem simpler from a data restoration standpoint.

It's fast, it's safe, it's easy to restore.
The big con is you loose 2 drives to redundancy which seems a high price to pay for safety, but is it? It depends on the data you keep sored on it.
Another way is having a 2TB external harddisk as backup and use the 4 500GB for every day use. Make a backup every few days/hours, whatever you find necessary. The first time it's hell, just let the PC work overnight. From then on it's only those files who were changed/added.
That's what I do with my 2 500GB drives.

---

### Post by KillerSiafu on 2010-12-06
> **lrgmmc said:**
> ok thats really similar to mine.
 
hdd1
------movies
--------0-9
--------a-m
 
 
hdd2
------movies
--------n-z
 
hdd3
------tvshows
--------0-9
--------a-m
 
hdd4
------tvshows
--------n-z
------Music
--------All
 
this way you have plenty of space for each catagory.

Ya I would have to adopt a system like this were I to keep the four drives as stand-alone drives. When I had them in a RAID array, there was no reason to have them split up into alphabetical sub-sets.

---

### Post by KillerSiafu on 2010-12-06
> **DeMus said:**
> It's fast, it's safe, it's easy to restore.
The big con is you loose 2 drives to redundancy which seems a high price to pay for safety, but is it? It depends on the data you keep sored on it.
Another way is having a 2TB external harddisk as backup and use the 4 500GB for every day use. Make a backup every few days/hours, whatever you find necessary. The first time it's hell, just let the PC work overnight. From then on it's only those files who were changed/added.
That's what I do with my 2 500GB drives.

Hm ya that might not be a bad approach either. As Irgmmc pointed out, I'd have to adopt a new organization method for that approach as it'd be doubtful that all my movies would fit onto one drive, etc. But that does keep my overall storage capacity up, which is nice.

---

### Post by lrgmmc on 2010-12-06
adapting to this method is not that hard. use of regular expreasions helps tons.

---

### Post by KillerSiafu on 2010-12-13
So I did go with the 4-independent disk method, using two 1TB drives as backup.

My initial impression of this, however, is that it is pretty tedious. I have to choose a location to download things to, which right now is drive A. However, most of my media won't live on drive A. So if it's a movie I'll move it to drive B or if it's a TV show I'll move it to drive C. The moving between drives is really pretty tedious. Before, when all the drives were in an array, I would just download the media and it was already on its final drive. Moving large files around between drives can take a long time.

I tried to figure out a good way to automate this, but it seems tricky to try and get an automated script to determine whether a file / folder is a movie and thus move it to drive B or a TV show and thus move it to drive C.

---

### Post by lrgmmc on 2010-12-13
what are the naming convintion of the files you are downloading? are they consistant?
ie tv shows start with S1E2 - title.avi or something else?

---

