---
title: "Problem with trash"
date: 2012-07-07
forum: General Help
---

### Post by DJDBgr on 2012-07-07
Hi. I'm having a problem with the trash can on ubuntu 12.04 23-bit. First time it occured i moved a big avi file (1GB) to the trash with some other files and tried emtying the trash by right clicking on it on the desktop and selecting "empty trash". Nothing happened and my desktop freezed. Everything else works properly while the desktop is stuck.

If i open up the trash and delete files one by one from there, there is no problem. The problem occurs when i try to empty the trash by right clicking on the shortcut of it on my desktop. Tried emptying it using terminal and nothing happened.

Plz help. Thanks in advance.

---

### Post by Rexilion on 2012-07-08
I also encounter issue's with trash. It's powered by some gvfsd-trash process that does 'stuff'. Sometimes it hangs causing thunar/nautilus/whatever to hang.

The files are actually stored in:

~/.local/share/Trash/files

and their info is stored at:

~/.local/share/Trash/info

Try purging the

~/.local/share/Trash

directory **effectively removing all of your files who reside in the trash can!**. And maybe a clean start fixes it?

---

