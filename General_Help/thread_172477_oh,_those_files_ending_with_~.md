---
title: "oh, those files ending with ~"
date: 2006-05-08
forum: General Help
---

### Post by Clouseau__ on 2006-05-08
Hi everyone.

I've a question about those files ending with ~,  (as in "index.php~") that are hidden by default. 

I'm assuming they're some auto-bakcups. I have some problems with them, however:

* They can be seen from KDE apps
* They can be seen (and get transfered) when I use GFtp
* I'm an order freak and don't like to have files that I didn't create in certain directories, even if I can't see them  :D

My question is the following: Assuming that I'm very careful and always backup my work, is it possible/safe to prevent these files from being created and clean the already existing ones?

Thanks a lot in advance!

Clouseau__

---

### Post by louis_nichols on 2006-05-08
Sure it's possible! I always deactivate the backup option in all editors that have it and have never regreted it. I press save to often to keep a genuinely original file as backup, anyway. To do this, every app has a preferences dialog, sometimes called options or settings. And the option for automatically creating backups is there somewhere.

---

### Post by aysiu on 2006-05-08
I would change the backup behavior from tacking on a ~ at the end to putting a . in the beginning.

Both KDE and Gnome hide folders and files that begin with .

---

### Post by Clouseau__ on 2006-05-08
Guys,

Thanks a lot!

I was going crazy searching the forums for this, since I thought this was a GNOME behavior and not a specific application one. I've already modified several app settings and it seems to have stopped.

Really, thanks a million  :)

Clouseau__

---

### Post by z_diver on 2006-05-08
[quote=aysiu]I would change the backup behavior from tacking on a ~ at the end to putting a . in the beginning.[/quote]
Does anyone know how to do this with gedit?

---

### Post by louis_nichols on 2006-05-09
[QUOTE=z_diver]Does anyone know how to do this with gedit?[/QUOTE]

Open Gedit, go to Edit>Preferences, then choose the tab "Editor" and uncheck, under "File saving", the option "Create a backup copy of files before saving"

---

