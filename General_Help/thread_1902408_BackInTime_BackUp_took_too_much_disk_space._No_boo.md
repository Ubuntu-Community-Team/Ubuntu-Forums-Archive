---
title: "BackInTime BackUp took too much disk space. No booting possible"
date: 2011-12-30
forum: General Help
---

### Post by wallone on 2011-12-30
Hi folks,
I used BackInTime the first time today. Wanted to backup my external hard drive on my laptop. I didn´t think a snapshot would take so much space so my hard drive went full till the last mb. I couldn´t delete the snapshot. Not even by terminal (ubuntu). Opening BIT with (root) said me sth like "X-Authorisation. sth sth not possible"  
Strangely I couldn t create more space by deleting other stuff on my drive although I stopped the back up process. I freed about 5 GB but it was still 0MB left. So I decided to restart which was my fault, cause since then I can t even boot my Ubuntu System. It stopps at the beginning telling me to login with an user (which it didn´t do before). I log in with my name : Nothing happens. Further more it sais sth about a problem with my energy configuration and  that s it.  So I am on my Windows now (which I fortunately kept) and I can´t even access to my Ubuntu files.  That ´s kinda sth I mind....
What to do?

---

### Post by jerrrys on 2011-12-31
You can use your Ubuntu Live CD to access/copy/move your files.  Just run the CD without installing.

As for what went wrong, I don't know.  Sorry, I do not use backintime.

I can tell you that I use clonezilla and Lucky Backup and grsync for backing up and they work fine.

[http://clonezilla.org/](http://clonezilla.org/)

Lucky Backup and grsync are in the software center.  Both products are a GUI for rsync which you already have installed by default.

[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

[http://en.wikipedia.org/wiki/Grsync](http://en.wikipedia.org/wiki/Grsync)

---

### Post by wallone on 2012-01-01
Thanks. That at least will solve the access problem. Moving and deleting files (the snaphot file) i guess won t be able there too...
But I ll first try to get myself a cd like that again and than. Start it.

---

### Post by wallone on 2012-01-02
Hi again.
Ok so I created a LIVE Ubuntu version on an USB drive and started the whole thing. I ve found the annoying back up file. But had also the idea to first delete some other files that take a lot of space, which I in the beginning didn t want to delete because they are of importance for me. But neither the first nor the other I could delete in the LIVE run lacking of root rights. How to continue?

---

### Post by jerrrys on 2012-01-02
Open a terminal and enter:

gksudo nautilus

that should give you access 

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+file+live+cd&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+file+live+cd&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=rm+command+remove+file&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=rm+command+remove+file&sa=Search&cof=FORID:9)

---

### Post by wallone on 2012-01-03
Oh dude...my thanks to you. I m back in my usual Ubuntu system. Could delete the snapshot with the gksudo command. Now I ll try again to Back Up but with clonezilla or sth similiar and definetly on another bigger hard drive.

P.S.: can t find the way how to mark it as solved.

---

### Post by jerrrys on 2012-01-03
congratulations :D

 [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mark+thread+as+solved&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mark+thread+as+solved&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=clean+file+system&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=clean+file+system&sa=Search&cof=FORID:9)

---

