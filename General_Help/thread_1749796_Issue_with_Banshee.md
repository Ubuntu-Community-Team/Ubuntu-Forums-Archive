---
title: "Issue with Banshee"
date: 2011-05-04
forum: General Help
---

### Post by ajtwin on 2011-05-04
So, I'm having an issue with the Banshee media player. I installed a package from the Ubuntu Software Center called "Earcandy" so that i could have the media player fade out when watching videos and such, but ever since i installed it, Banshee has been fast forwarding through everything i try to play. Whether it be songs or videos, it just fast forwards through everything without playing a sound. Pressing pause pauses the media, but when i press play again it resumes to fast forward. I uninstalled Earcandy and used Ubuntu Tweak to clear the remaining files, but it didnt help. I reinstalled Banshee, nothing. I even reinstalled the Ubuntu restricted extras in hopes that it would be a codec problem that would be fixed, still nothing. Any suggestions? All help is greatly appreciated.

Im using a clean install of Ubuntu 11.04 64bit

---

### Post by ivanovnegro on 2011-05-04
Maybe it would help to delete the config files of Banshee or the db (database).
You can fint it in your home folder but its hidden and the in .config or maybe you will see the Banshee folder just in your home folder.

---

### Post by ajtwin on 2011-05-04
> **ivanovnegro said:**
> Maybe it would help to delete the config files of Banshee or the db (database).
You can fint it in your home folder but its hidden and the in .config or maybe you will see the Banshee folder just in your home folder.

What exactly should i delete within that folder? Just config.xml?

---

### Post by ivanovnegro on 2011-05-04
So, you are in the .config folder. Yes, I think so, that will reset Banshee to the default status.

---

### Post by ajtwin on 2011-05-04
Unfortunately, that did not work. Any other suggestions?

---

### Post by Hedgehog1 on 2011-05-05
> **ajtwin said:**
> ...Banshee has been fast forwarding through everything i try to play. Whether it be songs or videos, it just fast forwards through everything without playing a sound...

This happened to me in Banshee; it was because I had not mounted the partition I keep my music on before starting Banshee.

If your music is stored on a partition that has been mounted under a new name, or on a partition that is not yet mounted you will see the same behavior.

***The Hedge***

:KS

---

### Post by ajtwin on 2011-05-05
> **Hedgehog1 said:**
> This happened to me in Banshee; it was because I had not mounted the partition I keep my music on before starting Banshee.

If your music is stored on a partition that has been mounted under a new name, or on a partition that is not yet mounted you will see the same behavior.

***The Hedge***

:KS

My music is indeed stored on a separate partition, but the partition is auto-mounted as soon as i login, before i start banshee. i tried unmounting and remounting the partition, but that didn't help either. Still haven't figured out how to solve this.

---

