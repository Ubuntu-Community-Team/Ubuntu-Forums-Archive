---
title: "32 bit sbackup not recognized by 64 bit Karmic"
date: 2010-04-10
forum: General Help
---

### Post by NateTut on 2010-04-10
I recently built a new system & installed 32 bit Karmic. After realizing that (doh!) I had a 64 bit processor I wanted to reinstall. So I first backed up with sbackup. All seemed to go well, the backup completed normally & I was able to open the backup with the archive manager with no problems.

So I installed 64 bit Ubuntu over top of the 32 bit version and all seemed to go well again with the 64 bit install. I install sbackup and try to open the 32 bit backup and it isn't recognized. I checked permissions and that is not the issue.

Any thoughts?

SOLVED!
          I needed to open the parent directory of the sbackup directory, not the sbackup directory itself.

---

