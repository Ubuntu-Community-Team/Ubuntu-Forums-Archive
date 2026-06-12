---
title: "Update manager incorrectly says &quot;updates available&quot;"
date: 2009-09-20
forum: General Help
---

### Post by oudalrich on 2009-09-20
Hi,

I've been having the following problem with update manager for the past few weeks: it keeps insisting that "updates are available" for my system, yet shows an empty list of updates. It even tells me that there are "788 KB" of downloads (cf screenshot). Clicking on "Install Updates" briefly shows the "Reading Package Information" windows, then update manager is back, still claiming there are updates.

When I do a "sudo aptitude safe-upgrade", it tells me there are 0 packages to upgrade.

I'm on Jaunty 32bit. I have disabled automatic startup of the update manager when updates are ready (reverting back to pre-Jaunty behaviour). The system is configured to check for updates once a day and notify me if there are any. The update notifications in the notification area still work as they should, i.e. the "pseudo update" is not advertised there.

Any ideas? I looked for a bug report that mentioned this, but found none. Couldn't find anything in the forums either.

Thanks in advance!

---

