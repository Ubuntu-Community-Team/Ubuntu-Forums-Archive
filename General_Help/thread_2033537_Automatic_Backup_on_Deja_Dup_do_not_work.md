---
title: "Automatic Backup on Deja Dup do not work"
date: 2012-07-26
forum: General Help
---

### Post by juanbuntu on 2012-07-26
I installed DejaDup under Ubuntu 11.10 and configured the tool for automatic backups.

Every time I create manual backups the tool works, but after several days I see no trace of automatic backups (I configured the tool for daily backups).

Has anyone else seen the same problem? Is there another forum to report this?

Thanks

---

### Post by CharlesA on 2012-07-26
Bumped to general help.

---

### Post by SteveTyrer on 2013-01-23
Hi, I have this same problem with 12.04, I can perform a manual backup but it will not work automatically can anyone help please?
  :D

---

### Post by pityu-kgc on 2013-09-13
I have the same with 12.10. Any idea?

---

### Post by pityu-kgc on 2013-09-13
Solved for me: go to Dashboard->Startup Applications and check in Backup Monitor. I might have deactivated it before.

---

### Post by CeejRab on 2013-09-15
Hello Juanbuntu, 

Be sure that the designated backup location exists. If you deleted the path where its supposed to back up to, this might keep it from performing the auto backup. 

If you back up to an external drive, make sure the drive is plugged in so that DejaDup can back up to it. 

When all else fails, do a manual backup to an external drive and reinstall. Although not the most tasteful option, Ubuntu is possibly one of the easiest OS's to install and get back to where you were quickly. I hope it doesn't come to that for you, but it is a last resort. 

All the best,

-Christian

---

