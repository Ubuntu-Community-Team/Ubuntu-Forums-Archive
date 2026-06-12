---
title: "Corrupted ext3 fillesystem"
date: 2010-02-09
forum: General Help
---

### Post by rob_w on 2010-02-09
I wasn't sure if this should go in General Help or Installation and Upgrades, so apologies if it's misplaced.

Yesterday I tried to install Ubuntu Netbook Remix alongside an existing Ubuntu install by repartitioning the hard drive. Something seemed to crash whilst the drive was being repartitioned, and when I tried to start the process again it got stuck on 0% - I left it running overnight with no change.

If I run the live image and look at that partition it says I don't have permission to view the files, but looking at disk usage it seems everything is still there. There's data on there I'd rather not lose (I know - should have backed up!). What do you recommend?

I considered trying to install Ubuntu into the existing swap partition and working from there... or is that just stupid?

---

### Post by mikewhatever on 2010-02-09
Having no permission doesn't indicate the file system is corrupted. Try **gksudo nautilus** while running from the cd. If the file system is corrupted, textdisk would be the tool to use.
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by rob_w on 2010-02-09
Looking at it via 'gksudo nautlus' the filesystem doesn't appear and clicking 'Computer' gives an error message saying "Nautilus cannot handle "computer" locations.".

I should also mention that parts of the filesystem are viewable and others give a permissions error.

---

