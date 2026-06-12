---
title: "Is there a simple roll-back for updates that break things?"
date: 2010-03-09
forum: General Help
---

### Post by slowman_x on 2010-03-09
There seems to be little clarity for the new user about this issue, but it seems to be an important one. I have had to resort to deleting my linux partition and reinstalling Ubuntu from my 9.10 ISO simply because some recommended updates via Update Manager completely trashed my previously perfect wifi network. No advice from this forum or googling could solve the problem, and I cannot find out how you revert to a previous state (like you can with System Restore in Windows) hence the drastic step. (Loading the original kernel via GRUB did not work either.) Since reinstalling from scratch GRUB is not as happy now as it was, but does load Ubuntu. 


[LIST]
[*]At the moment my Ubuntu wifi is fine again because I have the non-updated 9.10 version from the ISO
[*]Update Manager is prompting me to update again, naturally, but there is every chance it will break my wifi again if I do
[*]I'd try it if there was a simple roll-back option to rescue my system
[/LIST]
What should a newbie do in this situation?

---

### Post by dcstar on 2010-03-09
> **slowman_x said:**
> There seems to be little clarity for the new user about this issue, but it seems to be an important one. I have had to resort to deleting my linux partition and reinstalling Ubuntu from my 9.10 ISO simply because some recommended updates via Update Manager completely trashed my previously perfect wifi network. No advice from this forum or googling could solve the problem, and I cannot find out how you revert to a previous state (like you can with System Restore in Windows) hence the drastic step. (Loading the original kernel via GRUB did not work either.) Since reinstalling from scratch GRUB is not as happy now as it was, but does load Ubuntu. 


[LIST]
[*]At the moment my Ubuntu wifi is fine again because I have the non-updated 9.10 version from the ISO
[*]Update Manager is prompting me to update again, naturally, but there is every chance it will break my wifi again if I do
[*]I'd try it if there was a simple roll-back option to rescue my system
[/LIST]
What should a newbie do in this situation?

Synaptic will list all installed update packages, but you have to decide which ones you want to roll back. Synaptic will allow you to select any previously version that is still available and you can "Force Version" that package.

If you do not want certain packages to be updated, you can use "Lock Version" in Synaptic and they will no longer appear in the update list.

---

