---
title: "how to back up firefox plugins, bookmarks, add-ons and there preferences?"
date: 2009-08-10
forum: General Help
---

### Post by phr33k-dc on 2009-08-10
how do i do as per title so that when i reinstall ubuntu i will exactly the same forefox i had on my old install.

and i mean exactly the same. any help would be greatly appreciated as it is the only thing stopping me from installing ubuntu again.

thanks

---

### Post by any.linux12 on 2009-08-10
go to add-ons and install FEBE (Firefox environment backup extension)

---

### Post by Andreas1 on 2009-08-10
just take the hidden .mozilla folder stored in your home directory and put it in place again after you reinstalled your system

---

### Post by lovinglinux on 2009-08-10
+1 for FEBE

FEBE allows you to make regular backups automatically every number of days, every FF startup or shutdown and allows you keep a determined number of backup versions. It's really nice and a must-have extension.

Copying the profile folders inside ~/.mozilla/firefox also work.

You might like to read [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

Nevertheless, I strongly recommend that you setup a [separate partition for home](http://www.psychocats.net/ubuntu/separatehome). This will save you a lot of trouble on future upgrades. With a separate home partition you can install Ubuntu over an over, without loosing your configurations and personal files.

Also take a look at my [Umarks](https://addons.mozilla.org/en-US/firefox/addon/13153/) extension for Firefox. It allows you to create a list of all installed applications and then download and install them back, all-at-once, after you re-install Ubuntu.

---

### Post by phr33k-dc on 2009-08-10
wow thanks for the great ideas. Can you tell me how to partition my Home and how to restore it during a fresh install? Please

---

### Post by phr33k-dc on 2009-08-10
also if i was to do an encrypted install will it offer me the choice to have a seperate encrypted /Home partition aswell?

---

