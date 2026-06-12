---
title: "Right-click Disc 'Copy Disc...' .iso is stored where?"
date: 2009-11-28
forum: General Help
---

### Post by jamesisin on 2009-11-28
I have copied a few discs and now I am out of space on my OS drive.  Where does this (nameless?) application store its iso's while it is doing the copy work?

---

### Post by scouser73 on 2009-11-28
Check your **/home**

---

### Post by jamesisin on 2009-11-28
Nope.  That was my first stop.  There was an old Brasero iso in there, but that was all.  Since then I copied one more and there went another ~4.3 GB.  I'm not sure which application actually does the work when you right-click on the disc icon on the desktop, even knowing that might help me track these down.

---

### Post by jamesisin on 2009-11-29
Anybody else want to have a go at this?

---

### Post by Dinodoc on 2009-11-29
Looks like it might be cdrdao, but that may have changed I'm going from a bug report I found.  It seems to run:

launching command: cdrdao read-cd --read-raw --datafile /tmp/image.iso.V1WWVT --device /dev/hdc -v 2 /tmp/image.iso.V1WWVT.toc


so possibly try the /tmp/ folder?

---

### Post by apmcd47 on 2009-11-29
```
find ~ -name '*.iso' -print
sudo find / -name '*.iso' -print
```
The latter if the former doesn't find anything.

Andrew

---

### Post by jamesisin on 2009-11-29
They were in /tmp and one was called (just as an example) image.iso.IZWZ3U (there were three of them).  Hope that helps those who follow.

Andrew - Yours was a good suggestion; however, I would not have found anything with either (I'd have needed to use *.iso* I think).

---

### Post by 3rdalbum on 2009-11-29
As you've just discovered, things like that usually go into /tmp because they will be cleared on startup.

---

### Post by jamesisin on 2009-11-29
So everything in /tmp is dumped at startup?  I didn't know.  I did, however, know that rebooting would remove these files (but didn't want to have to take that measure).  Thanks for the tidbit.

---

