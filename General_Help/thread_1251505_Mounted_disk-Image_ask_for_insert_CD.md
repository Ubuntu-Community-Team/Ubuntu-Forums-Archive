---
title: "Mounted disk-Image ask for insert CD"
date: 2009-08-27
forum: General Help
---

### Post by niiize on 2009-08-27
I've got an ISO diskimage of a game I want to run from my harddrive instead of the CDROM. Now that it's mounted and I run it, It does start, but then ask me to insert the CD still.. ?


thnx

---

### Post by blueridgedog on 2009-08-27
Are you running this in wine, native Linux or in a virtual Windows OS?

---

### Post by niiize on 2009-08-28
Right, I run it in Wine, 1.1.28. 
The Windows version doen't seem to make any difference I might add

---

### Post by niiize on 2009-08-28
bumpp..

Though it might have something to do with fstab, but changing from cdrom0 to my mounted diskimage didn't affect anything eather. Hm

---

### Post by blueridgedog on 2009-08-28
So, mount your iso then tell wine it is a cdrom.  For example, mount the ISO at /mnt/mygame, then bring up your wine configuration (applications - Wine - configure wine) tool and click the drives tab, tell it to add a new drive (D:) and that the path is /mnt/mygame and that the type of mount is a CDROM.

And don't bump so soon...give people a chance to get home from work :-)

---

### Post by niiize on 2009-08-28
:)
Yep, exactly this I've tried. The ISO is there, and can be explored, and when I run the game I get the fullscreen graphicmode and then the game ask me to insert CD. 
Wine still not seem to find it. Might the directory "media" have some involvement

---

### Post by blueridgedog on 2009-08-28
So, you have given it the path to the mounted ISO image, told it to make it a cdrom and used drive letter "D".  Unfortunately you have run through my bag of tricks with wine.  Is it the same drive letter that you installed it from by chance?

---

### Post by niiize on 2009-08-29
Actually no. Did install it from the CD. Uninstalled, I tried to run the installation from the the D drive now, the ISO that is, but it prompts after a few secs for CD after klicking the executable. Better to start from there anyway.

---

