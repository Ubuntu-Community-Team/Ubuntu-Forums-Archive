---
title: "Settings in programmes cannot be saved"
date: 2009-12-13
forum: General Help
---

### Post by Diaboflo on 2009-12-13
Hi all,
I have a strange problems with some programs. They all work perfectly fine but when I close and start them all my settings are gone. Also the recent files menu is always empty after having restarted the programs. The problem happens with kate and kile, there  might be some others which I haven't found yet. Strangely there are no problems for example with firefox and openoffice. 
I checked in my home folder and there is no .kile and .kate folder but creating these folders didn't help.
Has anyone an idea what the problem might be?

Cheers,
Diaboflo

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
Check the permissions of the settings files. For example the settings for mozilla are in ~/.mozilla .

---

### Post by Diaboflo on 2009-12-14
Hi,
that doesn't seem to be the problem. There are simply no .kile and .kate folders. Creating them and activating rwx for all users didn't help either.

---

### Post by Zorael on 2009-12-14
KDE apps keep their settings in **~/.kde**, so that's the directory (and its subdirectories, particularly **share/config**) that you want to check the permissions of.

---

### Post by Diaboflo on 2009-12-17
Hi,
I checked the files, seems alright, I have read and write permissions. However kile always starts with an empty session, the recent files menu is always deactivated when I start the program. I can work with it but it is just an annoying detail that would be good to have...

Thanks for your answers so far, any ideas what I could do about this?

Diaboflo

---

### Post by Diaboflo on 2009-12-18
Hi all,
I think I was just being a bit stupid... The files I had opened were on an external hardrive which didn't automount, so the files weren't available after restarting my computer. Sorry for that! It works when I mount the hard drive before starting the programs.
Diaboflo

---

