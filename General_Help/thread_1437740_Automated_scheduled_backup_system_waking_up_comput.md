---
title: "Automated scheduled backup system waking up computers"
date: 2010-03-24
forum: General Help
---

### Post by gletscher on 2010-03-24
Hi I wasn't quite sure where to post this, so if it fits into another category, please move it.

I am looking for an automated backup system and I like bacula. I have 3 Notebooks and a Desktop computer that need regular backup. Now I don't want to let them run all night just to do the backuping, so I was thinking I could use wake-on-lan to have bacula wake up the machines, then do the backups, and shut them down afterswards. While this may work with devices on the ethernet, it won't work with the Notebooks on the wifi. So is it possible to have the Notebooks schedules to automatically wake up from suspend or shutdown ?

Or is it possible to interject a shutdown command if it is after a cerain hour and call the bacula director to start the backup now?

Thanks alot for your help, input and ideas.

Gletscher

---

### Post by tgalati4 on 2010-03-24
If the netbooks are running linux:

man crontab

Use BIOS wake, set cronjob to run at a time several minutes after wake.   The cronjob would include a sleep command after backup.

---

### Post by gletscher on 2010-03-25
thanks for the answer, will try it out.

---

