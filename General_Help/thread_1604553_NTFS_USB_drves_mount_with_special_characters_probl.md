---
title: "NTFS USB drves mount with special characters problem"
date: 2010-10-24
forum: General Help
---

### Post by MartinusEx on 2010-10-24
Hi out there,


I'm running mythbuntu 0.21 on a hardy environment.

I had a thread under mythbuntu but i think this was the wrong forum.
So here it is again

<lameexcuse> 
Currently i hesitate to upgrade to lucid because i fear problems coming up which i do not have the time to solve.
The machine works generally fine so why upgrade to lucid?
</lameexcuse> 
OK.

heres my problem 
I have 5 NTFS hard disks connected via USB and mount them via fstab

Now and then the drives refuse to accept special characters (ÄÖÜß and the like)
Now again it is the time.
i had some methods to get along, but nothing works at the moment and I got stuck.

I do not really have a clue how this all relates and what setting has an influence or not.
Its all best guess work here currently.

this is one of my lines in fstab, how I mount the 5 drives
```
UUID=123456789ABCD /media/VIDEO1 ntfs-3g -o  rw,users,owner,gid=100,uid=1000,dmask=0,umask=0 0 0

```

as i said I cannot save files or create folders with on special character to those drives.

One reply in the mythbuntu thread let me change the lines in fstab so it looks like this
```
UUID=123456789ABCD /media/VIDEO1 ntfs-3g **-o locale=de_DE@euro** rw,users,owner,gid=100,uid=1000,dmask=0,umask=0 0 0
```

THAT DOESN'T WORK.

I found something about using "-t ntfs.FUSE" but I don't know if that s good (I'll give it a try...)

But again its all guesswork and the lot of information is confusing to me at the very moment.

Does anyone have e clue how to solve this so that the NTFS drives again accept special characters.

Oh yes.. i already have some files and folder stored there which contain such characters.
Those files vanish from the ls output (Still there but not listed and not accessible)
 i hook such a hdd to my lucid machine and all comes out good.
But currently i refuse to upgrade.


thx for every hint.

Martin

---

### Post by MartinusEx on 2010-10-24
OK,

as usual .. once i get asking i find a way my self :)
Thanks for reading this :guitar:

Well it was NOT a NTFS or mounting problem.. but a language setting and UTF-8 unicode thing 
I really do not understand the relations but this I did and it worked

Add (if not there) /etc/profile.d/lang.sh 
if there's a line
```
export LANG=us_US
```
comment that out
```
#export LANG=us_US
```

insert (for germans)

```
export LANG=de_DE.UTF-8
```

if lang.sh was not there this is the only line
(i think the same is valid for aother europüean languages with special characters.

No problem with mount or ntfs-3g, which i found out was programmed NOT to translate languages anymore.

This solved my problem and now again I can create Folders with names like "ÄÜÖßÜÜ" 

again thanks for reading
Martin

---

### Post by MartinusEx on 2010-12-23
<update>

by some reason after I did the work on lang.sh the system again refused to work with umlaute.

I further read and found to add locale=de_DE.UTF-8
The point is, it has to be put in fstab  like

UUID=123456ADCBDFE /media/myvid ntfs-3g rw,users,owner,gid=100, uid=1000, dmask=0, umask=0, locale=de_DE.UTF-8 0 0

A lot of poeple stated the entry but never (at least in one thread i found it) WHERE to enter it correctly.
A lot of poeple assume that the reader is always so educated as to know all the rest, just the very command isn't there.

Unluckily it is often enough necessary to give more input and do NOT ASSUME that the inquiring reader knows all the rest :)

So THIS worked at least and i can use german umlauts even on my "old" 8.04 mythbuntu and a lot of poeple perefer to never use umlauts in filenames.
But when mythbuntu creates the folder automaticaly I do not want to edit every umlaut in mythbuntu.

So long and thx to all the poeple out there who share their knowledge
:popcorn:
</update>

---

### Post by JrRRr on 2011-07-03
Thanks for this solution, and that you posted it after you solved it. :)

I shall now try this solution, and by the looks of it (thanks for your extensive input) it should work..

---

