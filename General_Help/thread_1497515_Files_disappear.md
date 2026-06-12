---
title: "Files disappear"
date: 2010-05-30
forum: General Help
---

### Post by gortandklaatu on 2010-05-30
So, I convinced my husband (long-time PC user) to get a netbook and put Ubuntu on it. All is going well, except for this: he has had two important documents completely disappear. Both were OpenOffice docs (one was an Impress file, the other an .odt file). I searched his computer using the graphical search and through the command-line. No trace of the files. Not in any temporary folders and not in the OpenOffice backup folder. Both were new documents initiated from within OpenOffice, not downloaded from his email.
He runs Ubuntu 9.10 and keeps all of his files on his desktop.
Any ideas on what is going on and how to prevent this from happening again?

---

### Post by quadproc on 2010-05-30
> **gortandklaatu said:**
> So, I convinced my husband (long-time PC user) to get a netbook and put Ubuntu on it. All is going well, except for this: he has had two important documents completely disappear. Both were OpenOffice docs (one was an Impress file, the other an .odt file). I searched his computer using the graphical search and through the command-line. No trace of the files. Not in any temporary folders and not in the OpenOffice backup folder. Both were new documents initiated from within OpenOffice, not downloaded from his email.
He runs Ubuntu 9.10 and keeps all of his files on his desktop.
Any ideas on what is going on and how to prevent this from happening again?
Did you check in the trash?  It is possible that the files might have been accidentally moved to trash.

Did you use the nautilis search for file names?  That is the function available in Places > Search for files; you only need a portion of the file name so try for as few characters as possible while not getting flooded with irrelevant files.

It is also possible that the files were never saved to the Desktop or anywhere else in the first place.  Of cousrse, Openoffice won't let you quit without saving unless you specifically tell it to.

Was there any kind of removable media present on the system during the creation of the files?  If so then the files might have ended up there.

If a file were created in the /tmp directory then it would be automatically removed on a startup so using /tmp is not a good idea in general.

Side note: you have a great user name.  Good luck.

quadproc

---

