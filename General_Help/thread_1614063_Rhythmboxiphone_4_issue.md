---
title: "Rhythmbox/iphone 4 issue"
date: 2010-11-05
forum: General Help
---

### Post by RM305 on 2010-11-05
I just started using Ubuntu 10.10 so its new to me. I connected my iphone 4 to the laptop and when iphone is recognized it asks is i want to open Rhythmbox. Once I do that Rhythmbox shows my device on the left window and once I click on it, it shows my iphone 4 music library and allows me to listen to music off the iphone. When open my iphone 4 music on the phone later I realized the majority of all my album cover artwork that i had on it are now suddenly mixed up with the incorrect songs.  The only thing I had noticed as i was while I was listening to music while connected it said "Iphone Syncing". I don't know why because i didn't click on anything to do so, plus I didn't have any music in Rhythmbox library originally. What could of caused the album covers to be incorrectly switched around? How do I stop it from automatically syncing? . I'm guessing I could re-sync my iphone to my itunes library to fix the album cover screw up. I just don't want it to happen again.

---

### Post by searchfgold6789 on 2010-11-05
I would suggest purging and reinstalling rhythmbox:```
sudo apt-get purge rhythmbox
sudo apt-get install rythmbox
``` which can be done from a terminal window, from under accessories.

If that doesn't work, you might want to consider installing Wine, then installing [COLOR=Blue]_**[iTunes]("http://www.itunes.com")**_[/COLOR].

---

### Post by thatguruguy on 2010-11-05
> **searchfgold6789 said:**
> I would suggest purging and reinstalling rhythmbox:```
sudo apt-get purge rhythmbox
sudo apt-get install rythmbox
``` which can be done from a terminal window, from under accessories.

If that doesn't work, you might want to consider installing Wine, then installing [COLOR=Blue]_**[iTunes]("http://www.itunes.com")**_[/COLOR].

itunes doesn't work under Wine.

---

