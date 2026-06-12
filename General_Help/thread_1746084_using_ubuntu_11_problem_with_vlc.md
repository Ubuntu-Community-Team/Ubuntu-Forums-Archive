---
title: "using ubuntu 11 problem with vlc"
date: 2011-05-01
forum: General Help
---

### Post by ddimit on 2011-05-01
im using latest version of vlc for movies
when im playing movies with vlc it plays normal but after a while
my computer's hard disc starts to work very heavily all my linus system freezes and the only solution i have is to close vlc player with system monitor for stopping the freezing 
after a lot of tries of course
how can i fix that?
also i cannot hear any voices of the actors
all the sounds play correct except the voices of the people in the movie

finally i have found the solution 
thanks for the help

---

### Post by cymbaline42 on 2011-05-01
Try using The Totem Movie Player (also known simply as Movie Player), which is lighter on system resources than VLC. 

Point to Applications - Sound & Video - Movie Player to access it.

---

### Post by ddimit on 2011-05-01
even with movie player i cannot hear correctly the movie actors voices
i had that problem in past and it was the reason i stopped using linux and i went to windows
a friend told me that maybe they fixed that problem but like it looks the problem keep exists 
if noone can help me i will have to re-use windows
im very big fan of movies and i cannot stop watching just because of that problem

---

### Post by cymbaline42 on 2011-05-01
Do you have Ubuntu restricted extras installed?

If not, you can install it from the Software Center.

If it still persists, try this workaround: ([http://ubuntuforums.org/showpost.php?p=9948061&postcount=2)]("http://ubuntuforums.org/showpost.php?p=9948061&postcount=2")

---

### Post by ddimit on 2011-05-01
i have installed restricted extras from before 
i have changed the line to the corrects one 
restarted but i still hear the voice of people in movie lower than the other sounds 
lower than for example   music crash of cars etc

---

### Post by andreev on 2011-05-11
Hi ddimit,

I had the same problem after upgrading Ubuntu from version 10.10 to 11.04. Most probably it persists after the clean instalation too. The issue is in the memory management module which VLC is using by default. The reason your hard to work so heavy is a memory leak and the swap storage becomes full for a period of time.

You can fix the problem by selecting a specific memory module in VLC - MMX memcpy.
Additionally you should uncheck all CPU accelerators except the MMX support.

This should work on all CPUs.

---

