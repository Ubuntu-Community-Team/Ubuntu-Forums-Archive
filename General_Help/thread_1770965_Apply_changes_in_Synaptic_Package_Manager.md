---
title: "Apply changes in Synaptic Package Manager"
date: 2011-05-29
forum: General Help
---

### Post by Baloeb on 2011-05-29
I have some programs that I have already uninstalled, but that I now realize have left behind files on my computer.  I went to the package manager and selected them for complete removal, but the apply button will not work.  Same with ctrl P.  Is there a way to get it to completely erase these programs?  Is there a better way to go about this?

Thanks!

---

### Post by pSYcl0Ne on 2011-05-29
rightclick reveals options 'uninstall' and 'completely remove'

---

### Post by Baloeb on 2011-05-29
I've already gotten that far.  The problem is that these programs have already been uninstalled.  I still have the option to mark for complete removal but when I do there isn't a way to apply those changes.

---

### Post by NormanFLinux on 2011-05-29
You'll have to install something else to apply those changes.

---

### Post by jerrrys on 2011-05-29
theres **deborphan** for packages left behind, use with care.  but i wonder if you have not removed some dependences.  what packages have you removed?

---

### Post by Baloeb on 2011-05-29
I don't believe these are orphan packages.  For example I downloaded a few music players to try them out, then uninstalled them after I decided on what I liked.  So for example I uninstalled aqualung, but there is still an option in package manager to completely uninstall aqualung.  That is what I was trying to do.  I actually have one more question.  In my home folder there is still a .aqualung folder.  Is it safe to delete this since the package has been completely uninstalled?  Is there anywhere else on the computer that would have files left behind that should also be cleaned out?

---

### Post by linuxinstalledfromhdd on 2011-05-29
Yes, it would be in synaptic package manager. 

sudo synaptic

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

That should do the trick. :D

---

### Post by jerrrys on 2011-05-29
yes, that should do it.  but to be sure, open a terminal and enter

locate aqualung

---

