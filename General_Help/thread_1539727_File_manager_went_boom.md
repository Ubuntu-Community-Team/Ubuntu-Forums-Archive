---
title: "File manager went *boom*?"
date: 2010-07-26
forum: General Help
---

### Post by OpalGirl on 2010-07-26
After a bit of a scare with metacity disappearing after an update earlier, I got it back--only to discover that when I click a folder in my 'Files and Folders' section of the main menu, I get an error message:

 Unable to open [folder name]:

No application is registered as handling this file.

I did install nautilus-elementary via PPA a couple of days ago, but there was no problem at all until this evening.

If I launch nautilus from the alt-F2 run dialog, it works as normal, and I can browse folders within the window that pops up.

Ideas? A fix?

---

### Post by OpalGirl on 2010-07-26
The right combination of Google search terms helped me fix it--all by myself. A short fix, in case anyone else should run into a similar problem:

Run nautilus manually and browse to your home directory. Right-click one of the folders that won't open and select 'open with other application'. Select 'use custom command' and enter 'nautilus'.

---

### Post by rtimai on 2012-01-21
I'm currently experiencing the same errors, possibly after running the Computer Janitor integrated in Ubuntu Tweak.

My problem in Ubuntu 11.10 is there is no Open With Other Application option when right-clicking on a FOLDER. This appears only with files (and I know in *nix EVERYTHING is a file, but apparently not in Nautilus.)

Months ago, I used an application to adjust file and folder associations, but am unable to find it. Doesn't appear in the System Settings Panel in Ubuntu Unity.

Also, yes, Ubuntu Tweak has a restore system settings feature, but I'm afraid to use it, as I've recently uninstalled a number of desktop modules (LXDE alt desktop, w/ bundled related apps, etc.)

I'm sure there's a easy fix for this, but I'm stumped. Help, thanks.

---

