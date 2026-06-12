---
title: "Need help with Banshee"
date: 2011-08-21
forum: General Help
---

### Post by scottishbloke on 2011-08-21
It does not fetch my music data from any CD I put In my PC and Its a fresh Install, I have tried Installing rythmnbox and still get the same. Any suggestions greatly welcomed.

---

### Post by gordintoronto on 2011-08-21
I use Sound Juicer. Did you install the "restricted extras"? Can you play the CD using VLC Media Player?

When you insert a CD, does anything happen? Perhaps you could explain, "I do x and y and expect z to happen, but this other thing happens instead."

---

### Post by scottishbloke on 2011-08-22
Hi yes I should explain It better, Banshee can read my CD'S but It does not fetch the song titles or the album cover art. I have the restricted extras Installed.

---

### Post by gordintoronto on 2011-08-23
Does this happen with "popular" CDs? I have a low-volume boxed set which is not in the database, and it also (obviously) does not fetch any information for CDs I have made.

---

### Post by scottishbloke on 2011-08-23
Erm old and new I think, I done this (Edit -> preferences -> Write metadata to files in Banshee) But still no luck.

---

### Post by gordintoronto on 2011-08-23
All I can do is suggest Sound Juicer, which works for me.

One long-shot thought: are certain sites blocked on your computer, by some kind of "net nanny" software?

---

### Post by scottishbloke on 2011-08-24
No sites are blocked, I will try sound juicer, I am also going to try creating a last FM account and try and get the data fetched through that, Thanks for all your help.

Regards

Steve

---

### Post by mc4man on 2011-08-24
banshee has an issue with MusicBrainz that causes a high rate of failure to retrieve cd info.
A patch has been accepted that fixes this for most cd's, though it's not likely to show up in natty at this point.
While not in the 11.10 banshee atm it should be included before release.
(not sure if it's in a banshee ppa version 
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/813836](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/813836)

---

### Post by scottishbloke on 2011-08-24
Cheers mc4man :)

---

### Post by mc4man on 2011-08-24
Just if curious about natty - 
there was a natty bug on this that showed fix released and pointed to a SRU proposed update in natty.

Yet when testing and looking thru the source there was no fix for cdinfo and the performance was quite poor

Tried to address in the SRU bug, it turned into a bit of a circular headbanger so  I gave up and re-filed on 11.10 only
At some point, (if not already) the banshee ppa may be patched
(don't have the ppa url handy.

SRU bug
[https://bugs.launchpad.net/ubuntu/natty/+source/banshee/+bug/784179](https://bugs.launchpad.net/ubuntu/natty/+source/banshee/+bug/784179)

---

