---
title: "Ubuntu 12.10 update &gt; Need of manually updating external PPAs?"
date: 2012-09-17
forum: General Help
---

### Post by MrsUser on 2012-09-17
Hello dear Ubuntu users,

If I update to Ubuntu 12.10, do I have to (manually) update external PPAs as well?

For instance, I have some PPAs from webupd8 in my repositories. But they were meant for 12.04, right? So I assume I have to update the repos as well. Or is Ubuntu 'smart' enough to update these as well and replace 'Precise Pangolin' with 'Quantal Quetzal' in all the repo names?

Also, before updating - do I have to disable the external repos? I just want to make sure that nothing goes wrong during the update.

Thank you in advance :popcorn:

---

### Post by ajgreeny on 2012-09-17
As far as I'm aware it is recommended that you disable, or remove completely, all ppa references that you have in software sources before doing a distro update.

If you don't, I believe that you may get a lot of error messages when you try to do the update to the new distro version.  You may wish to look at the ppa-purge package which can do all this for you.

---

### Post by newb85 on 2012-09-17
It's been a few releases since I used the upgrade feature (instead of a fresh install).  Last time I did, though, having PPAs set up didn't cause any problems.  The upgrade automatically disabled them.

---

### Post by jrog on 2012-09-17
> **newb85 said:**
> It's been a few releases since I used the upgrade feature (instead of a fresh install).  Last time I did, though, having PPAs set up didn't cause any problems.  The upgrade automatically disabled them.
Having upgraded from 12.04 to 12.10 Beta in the last few days, I can say that the upgrade automatically disabled my PPAs as well.

---

### Post by MrsUser on 2012-09-17
Thanks for the infos!

But after the upgrade, do I have to update the PPAs manually?

---

### Post by newb85 on 2012-09-18
The old Repos will be disabled, and new ones will be added.

I believe you will have to edit the PPA entries to reflect the new release.  

I suppose that, alternatively, you could simply re-add the entries using the apt-add-repository command.  (Yes, in Quantal it's been changed from add-apt-repository to apt-add-repository.)

---

### Post by MrsUser on 2012-09-18
Thank you! I'll try as suggested and will disable the custom PPAs before upgrading.

---

