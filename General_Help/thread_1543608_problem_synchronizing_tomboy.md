---
title: "problem synchronizing tomboy"
date: 2010-08-01
forum: General Help
---

### Post by sa-mejia on 2010-08-01
I used to have my tomboy notes synchronized across machines by using Dropbox and having a soft link from ~\.tomboy -> ~\Dropbox\tomboy (I had never used the synchronization plug-in).

I have made a fresh install of ubuntu 10.4, but it seems that this version of tomboy is not any longer has ~\..tomboy as its main directory (instead it clutters the home directories with numbered directories.

I have tried to synchronize tomboy to my old tomboy notes, but unfortunately it has not worked (i.e. in the synchronization tab, I ask tomboy to use the folder of my the old tomboy notes that I have in my Dropbox folder (where all of my notes live), but it complains by claiming: "error connecting to the synchronization service".)

Any help is appreciated.

---

### Post by sa-mejia on 2010-08-01
SOLVED:

I found where the new directories are for tomboy are now kept and what is the environment variable that controls the note directory ([http://live.gnome.org/Tomboy/Directories](http://live.gnome.org/Tomboy/Directories)).

Thus, the best solution seems simply to assign TOMBOY_PATH to the file where you have your tomboy files (~/Dropbox/tomboy)


Another method (which, however, I have not tried) would have been to make a soft link from ~/.local/share/tomboy/ into ~/Dropbox/tomboy (I imagine it works, but I did not try it).

---

### Post by ajgreeny on 2010-08-01
The tomboy notes are cached in 10.04 in ~/.local/share/tomboy so you should still be able to sync with other machines, I think, if you use that folder.  This assumes that the format of the notes has not changed, and as I don't use tomboy, I can't comment about that possibility.

EDIT:
I see you have already found this information, but not tried it yet.

---

