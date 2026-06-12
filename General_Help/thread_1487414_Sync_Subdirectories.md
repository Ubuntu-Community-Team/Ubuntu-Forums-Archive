---
title: "Sync Subdirectories"
date: 2010-05-19
forum: General Help
---

### Post by greenleafthered on 2010-05-19
My wife and I are photographers, and we use an Ubuntu server to store all of the photos we take (as well as all our other files/backups/etc.) and I'm looking for a way to easily find the photos we've edited without wading through all the ones we haven't to get there.

Currently our photos are organized like this:
photos/<year>/<date>/Edited with the originals in the <date> directory and the edited ones in the Edited subdirectory.  What I would really like is to be able to run a script in cron to scan the photos directory and sync all the edited photos to a separate directory so that photos/<year>/<date>/Edited is synced to photoalbum/<year>/<date>.

I guess since both photos and photoalbum would reside on the same physical drive, a script to link the edited photos to the new location would work as well as syncing them.

Thanks in advance.

---

