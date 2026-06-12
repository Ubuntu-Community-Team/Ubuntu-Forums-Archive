---
title: "Sync Zune from network drive (VirtualBox)"
date: 2009-08-14
forum: General Help
---

### Post by wastingpenguins on 2009-08-14
Hi folks,

Fairly new to Linux, and loving it so far. The only thing holding me back is finding a way to sync my Zune without having to dual boot. VirtualBox seems like an elegant solution, and I've got it all up and running perfectly, except for this one problem, which is a BIG problem for me.

Breakdown: My music is all in the Ubuntu "Music" folder. Using VirtualBox shared folders, I have mapped that folder to a network drive within virtual XP. The Zune software reads the network just fine and I have my library all set up. Within Zune software I can browse and play all music files without problems. 

However, the music will not sync this way, for reasons unknown to me. At first I was totally baffled, but I found that my problem is identical to the one expressed in this thread: [http://forums.virtualbox.org/viewtopic.php?f=2&t=13094](http://forums.virtualbox.org/viewtopic.php?f=2&t=13094)

Turns out the Zune can't sync through network drives like that, for whatever reason. The author of that thread suggests I instead use Samba to set up shared folders. I followed this tutorial: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

After much tinkering, I successfully used Samba to set up a new shared folder between Ubuntu and virtual XP. However, setting up a *new* shared folder is useless to me -- I want my Ubuntu "Music" folder to be the shared folder, but I cannot get it to work. I presume it is only a matter of correctly setting up the Samba config file, but all my attempts were unsuccessful.

Thoughts/ideas/suggestions?

---

