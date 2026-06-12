---
title: "backintime problem"
date: 2012-01-14
forum: General Help
---

### Post by wog on 2012-01-14
I have a directory on /dev/shm I'm trying to backup regularly. 

Back In Time was suggested to me, and it seems to set up and run easily, but the operative word is *seems*. 

I cannot find the backed up files Back In Time says it is backing up. This means I can't restore those files when I need them.

I went to the documentation page for Back In Time, and while it positively glows on how easy Back In Time is to install and set up, it says nearly nothing about how to restore files backed up and how those files are saved.

Can anyone help me figure this out?

---

### Post by cottfcfan on 2012-01-14
Are they hidden files that you are backing up (the ones starting with a .)?
If so there is a setting in backintime to show hideen files, before you can restore them.
I also know that backintime did have a problem with files belonging to root, but I haven't used it for a while, so not sure if that's still the case.
If you get no joy try luckybackup, its in the repos, ive been using that for a while now with no problems.

---

### Post by wog on 2012-01-14
No, the files aren't hidden, and they're not owned by root.

Side Topic: I had a cron / rsync process doing backup before I brought in Back In Time, but it mysteriously stopped working after I upgraded to the latest version. I discovered the batch file doing the work had been set to non-functional status. I recently set that to functional status and ran it. The batch file does the work when manually entered, but although cron seems to be installed it doesn't seem to be calling the batch file or running it.

Will Back In Time conflict with any other backup solution? Do I need to uninstall Back In Time?

---

### Post by cottfcfan on 2012-01-15
You can have as many backup programs as you like as long as you only run one at a time. The only problem is you'll be duplicating backups in your source directory. But if space is no problem, it doesn't matter.
Try luckybackup.

---

