---
title: "Tips on cleaning up the HD?"
date: 2006-05-07
forum: General Help
---

### Post by glassgloss on 2006-05-07
Hey,

I am looking for some tips on cleaning up my hard drive.  I am down to about 4 gigs left, and since this is a 20 gig laptop hd, I am not all that concerned since I usually run with about 6 gigs left after a few games, music, etc.  I am just wanting to know what folders I can check for some straggling files that don't get deleted with normal processes?

---

### Post by sprinkles on 2006-05-07
[QUOTE=glassgloss]Hey,

I am looking for some tips on cleaning up my hard drive.  I am down to about 4 gigs left, and since this is a 20 gig laptop hd, I am not all that concerned since I usually run with about 6 gigs left after a few games, music, etc.  I am just wanting to know what folders I can check for some straggling files that don't get deleted with normal processes?[/QUOTE]

Go into Synaptic (System > Administration > Synaptic Package Manager), click Settings > Preferences, then click to the files tab and click "Delete cached package files".

Frred up about 300mb last time I did it.

---

### Post by bluevoodoo1 on 2006-05-07
You can do that from a terminal too

sudo apt-get clean

and

sudo apt-get autoclean

---

### Post by Engnome on 2006-05-07
Whoah!!! thx, cleared 800 mb in less than 4 seconds =D Now the big question: WTH was it doing there in the first place? Doesnt ubuntu feel that it is on a small partition? (60gb hdd, 14 gb ubuntu 32 gb windows 8 gb testing) That sux, i blame windows all the time for eating my disk space and now ubuntu does the same:confused:

---

### Post by glassgloss on 2006-05-07
thanks-- i am not sure how much i cleaned up cos I am downloading some music at the same time-- but I could hear it deleting things! :)

---

