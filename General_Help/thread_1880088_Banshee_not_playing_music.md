---
title: "Banshee not playing music"
date: 2011-11-12
forum: General Help
---

### Post by jackoneill87 on 2011-11-12
I just had a problem where banshee was refusing to play any of my music. A few other people seem to have been having this problem as well. I finally fixed it by purging and reinstalling banshee. Just thought I'd post in case anybody had the same problem.

Open a terminal and type
> sudo apt-get purge bansheeHit y when it asks you to confirm.

Once this is finished type
> sudo apt-get install bansheePress y to confirm.

It seems the problem is something to do with the banshee database located in ~/.config/banshee-1. Deleting the database and reimporting the music seems to have worked for others, but running apt-get purge will make sure.

Also, you can't uninstall and reinstall using the software center because that keeps your config files intact.

---

### Post by sirchmeister on 2011-12-03
Just thought I'd post this with a useful bump when I ran into this problem. It's very possible that if your music is stored on some other drive that it may not be mounted. In this case, Banshee won't tell you that it is not mounted and will not play anything. Make sure the drive is mounted before you try to play the music imported from that drive.

---

### Post by oldtimer7777 on 2011-12-03
Lately I had banshee on my computer and it froze a perfectly working system to the point where I had to do a hard shutdown from the power button on the box.  They removed it from the next release because of all the trouble recently too. 

> **jackoneill87 said:**
> I just had a problem where banshee was refusing to play any of my music. A few other people seem to have been having this problem as well. I finally fixed it by purging and reinstalling banshee. Just thought I'd post in case anybody had the same problem.

Open a terminal and type
Hit y when it asks you to confirm.

Once this is finished type
Press y to confirm.

It seems the problem is something to do with the banshee database located in ~/.config/banshee-1. Deleting the database and reimporting the music seems to have worked for others, but running apt-get purge will make sure.

Also, you can't uninstall and reinstall using the software center because that keeps your config files intact.

---

