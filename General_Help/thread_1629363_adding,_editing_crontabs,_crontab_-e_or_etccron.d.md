---
title: "adding, editing crontabs, crontab -e or /etc/cron.d ?"
date: 2010-11-23
forum: General Help
---

### Post by damang111 on 2010-11-23
I was always confused as to where the best place to put cron jobs would be.
Would it be in the crontab -e editor or add/edit the cron files manually in /etc/cron.d ?

I was under the impression both should work fine.
However I'm working on a linux box that has some things in /etc/cron.d but it never gets run.
Crontabs on this machine only run when editing directly from crontab -e  .

why is this?

tia.

---

### Post by Cheesehead on 2010-11-23
cron does not look for crontabs in /etc/cron.d, so anything you place there will be ignored.

If you want a cron job to run as a user (change my desktop picture, e-mail my brother, check my IP address, archive my favorite websites, backup my /home, etc), then use crontab -e to edit your user-level crontab. User-level crontabs are stored in /var/spool/cron/crontabs, but DON'T edit it directly. The crontab command not only enables editing, it also checks your syntax and tells cron to reload the completed crontab.

If you want a cron job to run as root (rotate logs, mount devices, change network connections, install updates, backup the complete system, etc) then edit the root crontab at /etc/crontab. Most common root-level jobs can be done even more easily by putting the job (or a link) in the /etc/cron/hourly or daily or weekly or monthly folders instead of mucking about with editing.

I've got a dozen or so custom cron jobs, nearly all user-level. The few that need to be root are all hourly or daily, so I've never needed to edit the root crontab at all.

---

### Post by matt_symes on 2010-11-23
Hi

Reading this might explain alot.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

It explains cron under user and root and anacron.

Kind regards

---

