---
title: "Do Ubuntu sources upgrade with the distro version?"
date: 2012-06-04
forum: General Help
---

### Post by unitedanarchy on 2012-06-04
I am on Ubuntu 11.10 and kind of scared of upgrading to 12.04, I really really don't want to have to go through my sources one by one changing oneiric to percise, Does Ubuntu do this itself? If not, Is there something that will do it for me?

---

### Post by mcduck on 2012-06-04
> **unitedanarchy said:**
> I am on Ubuntu 11.10 and kind of scared of upgrading to 12.04, I really really don't want to have to go through my sources one by one changing oneiric to percise, Does Ubuntu do this itself? If not, Is there something that will do it for me?

If you do the upgrade using Update Manager (or the "do-release-upgrade" command in terminal), then  the sources.list will be automatically updated for any official repositories. Any third-party repositories (like PPA's) will get commented out as there is no reliable way to determine if a certain third-party repository offers packages for the new release or not, so you'll have to handle those sources manually.

...on the other hand, even in worst cases editing the sources manually shouldn't take more than couple of minutes to do, so I really wouldn't see that as a reason to be afraid of upgrading. (and if you are sure all your repositories do provide packages for 12.04, you could always use some tool to automatically search&replace the distro name. Every decent text editor has that option, and of course there's always sed if you want to do it from command line...)

---

