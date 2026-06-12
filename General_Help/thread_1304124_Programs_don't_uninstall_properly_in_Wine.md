---
title: "Programs don't uninstall properly in Wine"
date: 2009-10-28
forum: General Help
---

### Post by nmyrick on 2009-10-28
I have some programs that I tried to install with Wine, and they did not install correctly, and now they won't uninstall.  Even if I go into the "c" drive and delete the files, they magically reappear after a restart.  The programs are "Smart Technologies (for smartboards), iTunes, and Quicktime.  I would like to get these off of my drive, or get them to install properly.

Thanks,
nmyrick:guitar:

---

### Post by Aemaeth on 2009-10-29
If you dont have anything in wine to lose then you could always 

sudo apt-get autoremove wine

also remember to remove the hidden config stuff with ctrl+h from the home directory. something like .wine 

Cheers!

---

### Post by DouglasAWh on 2009-10-29
> **nmyrick said:**
> I have some programs that I tried to install with Wine, and they did not install correctly, and now they won't uninstall.  Even if I go into the "c" drive and delete the files, they magically reappear after a restart.  The programs are "Smart Technologies (for smartboards), iTunes, and Quicktime.  I would like to get these off of my drive, or get them to install properly.

Thanks,
nmyrick:guitar:

You should be able to go to the files either in Nautilus or the terminal and remove them.  In might be easiest to do in terminal since you might have to be sudo.

For the record, I've seen apps in WINE be a PITA to uninstall also.  Never bothered me enough to look into it though. :)  I needed to free up some space and I did it through other means.

---

### Post by TheForumTroll on 2009-10-29
You could give PlayOnLinux a try :KS

---

