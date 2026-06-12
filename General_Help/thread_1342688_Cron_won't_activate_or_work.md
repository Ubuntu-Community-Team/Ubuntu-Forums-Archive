---
title: "Cron won't activate or work"
date: 2009-12-01
forum: General Help
---

### Post by lmicu on 2009-12-01
OK, (frustrated)

I have searched enought, I am trying to set up my file server and I got the Karmic Server. All is ok but cant find a way to make cron work for me. It seems like it ignores me. I will post the crontab -l and some more inf to see if I am doing something wrong.

This is crontab -l

root@server:/media/500# crontab -l
# m h  dom mon dow   command

42 12 * * * tar pzcf /media/500/lucian_storage_backup/lucian_`date '+%m%d%y'`.tgz /home/lucian/storage/*

40 7 * * * tar pzcf /media/500/mlv_storage_backup/mlv_`date '+%m%d%y'`.tgz /home/mlv/storage/*

54 12 * * * tar pzcf /media/500/miriam_storage_backup/miriam_`date '+%m%d%y'`.tgz /home/miriam/storage/*

40 7 * * * tar pzcf /media/500/delia_storage_backup/delia_`date '+%m%d%y'`.tgz /home/delia/storage/*

40 7 * * * tar pzcf /media/500/allen_storage_backup/allen_`date '+%m%d%y'`.tgz /home/allen/storage/*
root@server:/media/500#

This is the mail after cron suppose to tell me anything:

root@server:/media/500# mail
No mail for root
root@server:/media/500# 

Checked if cron is running:

ps ax | grep cron
1077 ?        Ss     0:00 cron
21983 pts/1    S+     0:00 grep cron


More details:

/media/500 is an usb hard drive and I am trying to backup some stuff on it.

all the other users will have their "storage" folder backed - up on the external drive.

Ignore the dates, I played around with them, I actually want to do a backup every Sunday night at 3 am. 

I bet is something easy ....... :-k

---

### Post by john newbuntu on 2009-12-01
Check /var/log/syslogs if cron ran these jobs.
grep -i cron /var/log/syslogs
I do not see a mailx or mail or sendmail command in your crontab file.  So how would a mail get sent?

---

### Post by lmicu on 2009-12-01
root@server:/media/500# grep -i cron /var/log/syslogs
grep: /var/log/syslogs: No such file or directory

WHat does this mean?

Should I run the command in a diffrent way?


BTW: Pretty new in Linux, try to hang in here!

---

### Post by raktarok on 2009-12-01
Hate to point it out, but I believe it should only be syslog, not syslogs.

I don't know if this will help,but try putting the lines in the file /etc/crontab. Don't forget to put the username after the time entries.

---

### Post by lmicu on 2009-12-01
> **raktarok said:**
> Hate to point it out, but I believe it should only be syslog, not syslogs.

got it, my bad:

in the eman time I made some additions (like I put the root as user in there - read it from a different post) here is what I have now

root@server:/var/log# cat syslog
Nov 30 06:29:20 server rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="735" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 30 06:50:05 server sudo: pam_sm_authenticate: Called
Nov 30 06:50:05 server sudo: pam_sm_authenticate: username = [lucian]
Nov 30 06:52:11 server crontab[15889]: (root) BEGIN EDIT (root)
Nov 30 06:54:09 server crontab[15889]: (root) REPLACE (root)
Nov 30 06:54:09 server crontab[15889]: (root) END EDIT (root)
Nov 30 06:55:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 06:56:15 server crontab[15907]: (root) BEGIN EDIT (root)
Nov 30 06:57:22 server crontab[15907]: (root) REPLACE (root)
Nov 30 06:57:22 server crontab[15907]: (root) END EDIT (root)
Nov 30 06:58:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:04:23 server crontab[15947]: (root) BEGIN EDIT (root)
Nov 30 07:05:12 server crontab[15947]: (root) REPLACE (root)
Nov 30 07:05:12 server crontab[15947]: (root) END EDIT (root)
Nov 30 07:06:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:17:01 server CRON[15998]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 07:32:03 server crontab[16055]: (root) LIST (root)
Nov 30 07:32:39 server crontab[16062]: (root) LIST (root)
Nov 30 07:36:52 server crontab[16078]: (root) BEGIN EDIT (root)
Nov 30 07:37:31 server crontab[16078]: (root) REPLACE (root)
Nov 30 07:37:31 server crontab[16078]: (root) END EDIT (root)
Nov 30 07:38:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:39:01 server CRON[16104]: (root) CMD (tar pzcf /media/500/lucian_storage_backup/lucian_`date '+)
Nov 30 07:39:36 server crontab[16117]: (root) LIST (root)
Nov 30 07:40:01 server CRON[16124]: (root) CMD (tar pzcf /media/500/allen_storage_backup/allen_`date '+)
Nov 30 07:40:01 server CRON[16127]: (root) CMD (tar pzcf /media/500/delia_storage_backup/delia_`date '+)
Nov 30 07:40:01 server CRON[16130]: (root) CMD (tar pzcf /media/500/mlv_storage_backup/mlv_`date '+)
Nov 30 07:40:01 server CRON[16133]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Nov 30 08:17:01 server CRON[16263]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 09:17:01 server CRON[16447]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 10:17:01 server CRON[16630]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 11:17:01 server CRON[16812]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 12:17:01 server CRON[16995]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 13:17:01 server CRON[17178]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 14:17:01 server CRON[17361]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 15:17:01 server CRON[17543]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 16:17:02 server CRON[17727]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 17:17:01 server CRON[17908]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 18:13:15 server sudo: pam_sm_authenticate: Called
Nov 30 18:13:15 server sudo: pam_sm_authenticate: username = [lucian]
Nov 30 18:13:26 server crontab[18147]: (root) BEGIN EDIT (root)
Nov 30 18:17:01 server CRON[18163]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 18:20:02 server crontab[18147]: (root) END EDIT (root)
Nov 30 19:17:01 server CRON[18365]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 20:17:01 server CRON[18556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 21:17:01 server CRON[18771]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 22:17:01 server CRON[18973]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 23:17:01 server CRON[19173]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 00:17:01 server CRON[19393]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 00:35:38 server sudo: pam_sm_authenticate: Called
Dec  1 00:35:38 server sudo: pam_sm_authenticate: username = [lucian]
Dec  1 00:36:39 server crontab[19553]: (root) BEGIN EDIT (root)
Dec  1 00:37:45 server crontab[19553]: (root) END EDIT (root)
Dec  1 00:41:14 server crontab[19578]: (root) LIST (root)
Dec  1 00:41:21 server crontab[19581]: (root) BEGIN EDIT (root)
Dec  1 00:42:06 server crontab[19581]: (root) REPLACE (root)
Dec  1 00:42:06 server crontab[19581]: (root) END EDIT (root)
Dec  1 00:42:22 server crontab[19592]: (root) LIST (root)
Dec  1 00:42:47 server sudo: pam_sm_authenticate: Called
Dec  1 00:42:47 server sudo: pam_sm_authenticate: username = [lucian]
Dec  1 00:43:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 00:43:17 server crontab[19677]: (root) BEGIN EDIT (root)
Dec  1 00:47:29 server postfix/master[20366]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec  1 00:47:54 server postfix/postfix-script[20384]: error: unknown command: ''
Dec  1 00:47:54 server postfix/postfix-script[20385]: fatal: usage: postfix start (or stop, reload, abort, flush, check, status, set-permissions, upgrade-configuration)
Dec  1 00:49:12 server postfix/master[20366]: terminating on signal 15
Dec  1 00:51:08 server postfix/master[20681]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec  1 00:52:49 server postfix/master[20681]: terminating on signal 15
Dec  1 00:53:37 server crontab[19677]: (root) REPLACE (root)
Dec  1 00:53:37 server crontab[19677]: (root) END EDIT (root)
Dec  1 00:54:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 00:59:02 server cron[21891]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 1077: Resource temporarily unavailable)
Dec  1 00:59:11 server cron[21895]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 1077: Resource temporarily unavailable)
Dec  1 01:00:59 server crontab[21903]: (root) LIST (root)
Dec  1 01:17:01 server CRON[21965]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 01:25:58 server crontab[22007]: (root) BEGIN EDIT (root)
Dec  1 01:26:34 server crontab[22007]: (root) REPLACE (root)
Dec  1 01:26:34 server crontab[22007]: (root) END EDIT (root)
Dec  1 01:26:48 server crontab[22017]: (root) LIST (root)
Dec  1 01:27:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:27:01 server CRON[22022]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 01:28:21 server crontab[22040]: (root) BEGIN EDIT (root)
Dec  1 01:28:48 server crontab[22040]: (root) REPLACE (root)
Dec  1 01:28:48 server crontab[22040]: (root) END EDIT (root)
Dec  1 01:28:49 server crontab[22046]: (root) BEGIN EDIT (root)
Dec  1 01:28:56 server crontab[22046]: (root) REPLACE (root)
Dec  1 01:28:56 server crontab[22046]: (root) END EDIT (root)
Dec  1 01:29:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:29:01 server CRON[22052]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 01:29:13 server crontab[22060]: (root) LIST (root)
Dec  1 01:29:18 server crontab[22062]: (root) BEGIN EDIT (root)
Dec  1 01:29:26 server crontab[22062]: (root) REPLACE (root)
Dec  1 01:29:26 server crontab[22062]: (root) END EDIT (root)
Dec  1 01:30:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:30:01 server CRON[22072]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
root@server:/var/log# grep -i cron /var/log/syslog
Nov 30 06:52:11 server crontab[15889]: (root) BEGIN EDIT (root)
Nov 30 06:54:09 server crontab[15889]: (root) REPLACE (root)
Nov 30 06:54:09 server crontab[15889]: (root) END EDIT (root)
Nov 30 06:55:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 06:56:15 server crontab[15907]: (root) BEGIN EDIT (root)
Nov 30 06:57:22 server crontab[15907]: (root) REPLACE (root)
Nov 30 06:57:22 server crontab[15907]: (root) END EDIT (root)
Nov 30 06:58:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:04:23 server crontab[15947]: (root) BEGIN EDIT (root)
Nov 30 07:05:12 server crontab[15947]: (root) REPLACE (root)
Nov 30 07:05:12 server crontab[15947]: (root) END EDIT (root)
Nov 30 07:06:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:17:01 server CRON[15998]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 07:32:03 server crontab[16055]: (root) LIST (root)
Nov 30 07:32:39 server crontab[16062]: (root) LIST (root)
Nov 30 07:36:52 server crontab[16078]: (root) BEGIN EDIT (root)
Nov 30 07:37:31 server crontab[16078]: (root) REPLACE (root)
Nov 30 07:37:31 server crontab[16078]: (root) END EDIT (root)
Nov 30 07:38:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:39:01 server CRON[16104]: (root) CMD (tar pzcf /media/500/lucian_storage_backup/lucian_`date '+)
Nov 30 07:39:36 server crontab[16117]: (root) LIST (root)
Nov 30 07:40:01 server CRON[16124]: (root) CMD (tar pzcf /media/500/allen_storage_backup/allen_`date '+)
Nov 30 07:40:01 server CRON[16127]: (root) CMD (tar pzcf /media/500/delia_storage_backup/delia_`date '+)
Nov 30 07:40:01 server CRON[16130]: (root) CMD (tar pzcf /media/500/mlv_storage_backup/mlv_`date '+)
Nov 30 07:40:01 server CRON[16133]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Nov 30 08:17:01 server CRON[16263]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 09:17:01 server CRON[16447]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 10:17:01 server CRON[16630]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 11:17:01 server CRON[16812]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 12:17:01 server CRON[16995]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 13:17:01 server CRON[17178]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 14:17:01 server CRON[17361]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 15:17:01 server CRON[17543]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 16:17:02 server CRON[17727]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 17:17:01 server CRON[17908]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 18:13:26 server crontab[18147]: (root) BEGIN EDIT (root)
Nov 30 18:17:01 server CRON[18163]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 18:20:02 server crontab[18147]: (root) END EDIT (root)
Nov 30 19:17:01 server CRON[18365]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 20:17:01 server CRON[18556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 21:17:01 server CRON[18771]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 22:17:01 server CRON[18973]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 23:17:01 server CRON[19173]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 00:17:01 server CRON[19393]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 00:36:39 server crontab[19553]: (root) BEGIN EDIT (root)
Dec  1 00:37:45 server crontab[19553]: (root) END EDIT (root)
Dec  1 00:41:14 server crontab[19578]: (root) LIST (root)
Dec  1 00:41:21 server crontab[19581]: (root) BEGIN EDIT (root)
Dec  1 00:42:06 server crontab[19581]: (root) REPLACE (root)
Dec  1 00:42:06 server crontab[19581]: (root) END EDIT (root)
Dec  1 00:42:22 server crontab[19592]: (root) LIST (root)
Dec  1 00:43:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 00:43:17 server crontab[19677]: (root) BEGIN EDIT (root)
Dec  1 00:53:37 server crontab[19677]: (root) REPLACE (root)
Dec  1 00:53:37 server crontab[19677]: (root) END EDIT (root)
Dec  1 00:54:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 00:59:02 server cron[21891]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 1077: Resource temporarily unavailable)
Dec  1 00:59:11 server cron[21895]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 1077: Resource temporarily unavailable)
Dec  1 01:00:59 server crontab[21903]: (root) LIST (root)
Dec  1 01:17:01 server CRON[21965]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 01:25:58 server crontab[22007]: (root) BEGIN EDIT (root)
Dec  1 01:26:34 server crontab[22007]: (root) REPLACE (root)
Dec  1 01:26:34 server crontab[22007]: (root) END EDIT (root)
Dec  1 01:26:48 server crontab[22017]: (root) LIST (root)
Dec  1 01:27:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:27:01 server CRON[22022]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 01:28:21 server crontab[22040]: (root) BEGIN EDIT (root)
Dec  1 01:28:48 server crontab[22040]: (root) REPLACE (root)
Dec  1 01:28:48 server crontab[22040]: (root) END EDIT (root)
Dec  1 01:28:49 server crontab[22046]: (root) BEGIN EDIT (root)
Dec  1 01:28:56 server crontab[22046]: (root) REPLACE (root)
Dec  1 01:28:56 server crontab[22046]: (root) END EDIT (root)
Dec  1 01:29:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:29:01 server CRON[22052]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 01:29:13 server crontab[22060]: (root) LIST (root)
Dec  1 01:29:18 server crontab[22062]: (root) BEGIN EDIT (root)
Dec  1 01:29:26 server crontab[22062]: (root) REPLACE (root)
Dec  1 01:29:26 server crontab[22062]: (root) END EDIT (root)
Dec  1 01:30:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:30:01 server CRON[22072]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
root@server:/var/log#




AND here i revert the changes:

root@server:/var/log# grep -i cron /var/log/syslog
Nov 30 06:52:11 server crontab[15889]: (root) BEGIN EDIT (root)
Nov 30 06:54:09 server crontab[15889]: (root) REPLACE (root)
Nov 30 06:54:09 server crontab[15889]: (root) END EDIT (root)
Nov 30 06:55:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 06:56:15 server crontab[15907]: (root) BEGIN EDIT (root)
Nov 30 06:57:22 server crontab[15907]: (root) REPLACE (root)
Nov 30 06:57:22 server crontab[15907]: (root) END EDIT (root)
Nov 30 06:58:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:04:23 server crontab[15947]: (root) BEGIN EDIT (root)
Nov 30 07:05:12 server crontab[15947]: (root) REPLACE (root)
Nov 30 07:05:12 server crontab[15947]: (root) END EDIT (root)
Nov 30 07:06:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:17:01 server CRON[15998]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 07:32:03 server crontab[16055]: (root) LIST (root)
Nov 30 07:32:39 server crontab[16062]: (root) LIST (root)
Nov 30 07:36:52 server crontab[16078]: (root) BEGIN EDIT (root)
Nov 30 07:37:31 server crontab[16078]: (root) REPLACE (root)
Nov 30 07:37:31 server crontab[16078]: (root) END EDIT (root)
Nov 30 07:38:01 server cron[1077]: (root) RELOAD (crontabs/root)
Nov 30 07:39:01 server CRON[16104]: (root) CMD (tar pzcf /media/500/lucian_storage_backup/lucian_`date '+)
Nov 30 07:39:36 server crontab[16117]: (root) LIST (root)
Nov 30 07:40:01 server CRON[16124]: (root) CMD (tar pzcf /media/500/allen_storage_backup/allen_`date '+)
Nov 30 07:40:01 server CRON[16127]: (root) CMD (tar pzcf /media/500/delia_storage_backup/delia_`date '+)
Nov 30 07:40:01 server CRON[16130]: (root) CMD (tar pzcf /media/500/mlv_storage_backup/mlv_`date '+)
Nov 30 07:40:01 server CRON[16133]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Nov 30 08:17:01 server CRON[16263]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 09:17:01 server CRON[16447]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 10:17:01 server CRON[16630]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 11:17:01 server CRON[16812]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 12:17:01 server CRON[16995]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 13:17:01 server CRON[17178]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 14:17:01 server CRON[17361]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 15:17:01 server CRON[17543]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 16:17:02 server CRON[17727]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 17:17:01 server CRON[17908]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 18:13:26 server crontab[18147]: (root) BEGIN EDIT (root)
Nov 30 18:17:01 server CRON[18163]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 18:20:02 server crontab[18147]: (root) END EDIT (root)
Nov 30 19:17:01 server CRON[18365]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 20:17:01 server CRON[18556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 21:17:01 server CRON[18771]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 22:17:01 server CRON[18973]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 23:17:01 server CRON[19173]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 00:17:01 server CRON[19393]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 00:36:39 server crontab[19553]: (root) BEGIN EDIT (root)
Dec  1 00:37:45 server crontab[19553]: (root) END EDIT (root)
Dec  1 00:41:14 server crontab[19578]: (root) LIST (root)
Dec  1 00:41:21 server crontab[19581]: (root) BEGIN EDIT (root)
Dec  1 00:42:06 server crontab[19581]: (root) REPLACE (root)
Dec  1 00:42:06 server crontab[19581]: (root) END EDIT (root)
Dec  1 00:42:22 server crontab[19592]: (root) LIST (root)
Dec  1 00:43:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 00:43:17 server crontab[19677]: (root) BEGIN EDIT (root)
Dec  1 00:53:37 server crontab[19677]: (root) REPLACE (root)
Dec  1 00:53:37 server crontab[19677]: (root) END EDIT (root)
Dec  1 00:54:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 00:59:02 server cron[21891]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 1077: Resource temporarily unavailable)
Dec  1 00:59:11 server cron[21895]: (CRON) DEATH (can't lock /var/run/crond.pid, otherpid may be 1077: Resource temporarily unavailable)
Dec  1 01:00:59 server crontab[21903]: (root) LIST (root)
Dec  1 01:17:01 server CRON[21965]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 01:25:58 server crontab[22007]: (root) BEGIN EDIT (root)
Dec  1 01:26:34 server crontab[22007]: (root) REPLACE (root)
Dec  1 01:26:34 server crontab[22007]: (root) END EDIT (root)
Dec  1 01:26:48 server crontab[22017]: (root) LIST (root)
Dec  1 01:27:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:27:01 server CRON[22022]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 01:28:21 server crontab[22040]: (root) BEGIN EDIT (root)
Dec  1 01:28:48 server crontab[22040]: (root) REPLACE (root)
Dec  1 01:28:48 server crontab[22040]: (root) END EDIT (root)
Dec  1 01:28:49 server crontab[22046]: (root) BEGIN EDIT (root)
Dec  1 01:28:56 server crontab[22046]: (root) REPLACE (root)
Dec  1 01:28:56 server crontab[22046]: (root) END EDIT (root)
Dec  1 01:29:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:29:01 server CRON[22052]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 01:29:13 server crontab[22060]: (root) LIST (root)
Dec  1 01:29:18 server crontab[22062]: (root) BEGIN EDIT (root)
Dec  1 01:29:26 server crontab[22062]: (root) REPLACE (root)
Dec  1 01:29:26 server crontab[22062]: (root) END EDIT (root)
Dec  1 01:30:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:30:01 server CRON[22072]: (root) CMD (root tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 01:39:40 server crontab[22124]: (root) LIST (root)
Dec  1 01:39:42 server crontab[22126]: (root) BEGIN EDIT (root)
Dec  1 01:40:18 server crontab[22126]: (root) REPLACE (root)
Dec  1 01:40:18 server crontab[22126]: (root) END EDIT (root)
Dec  1 01:40:20 server crontab[22131]: (root) BEGIN EDIT (root)
Dec  1 01:40:30 server crontab[22131]: (root) REPLACE (root)
Dec  1 01:40:30 server crontab[22131]: (root) END EDIT (root)
Dec  1 01:40:35 server crontab[22136]: (root) BEGIN EDIT (root)
Dec  1 01:40:39 server crontab[22136]: (root) REPLACE (root)
Dec  1 01:40:39 server crontab[22136]: (root) END EDIT (root)
Dec  1 01:41:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 01:41:01 server CRON[22145]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)

---

### Post by lmicu on 2009-12-01
> **raktarok said:**
> Hate to point it out, but I believe it should only be syslog, not syslogs.

I don't know if this will help,but try putting the lines in the file /etc/crontab. Don't forget to put the username after the time entries.

root@server:/media/500/miriam_storage_backup# cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

AM I missing something here? Isn't this suppose to work?


And if I put the lines straight in the /etc/crotab how should I relod the corn deamon? or I should just restart the server?

---

### Post by raktarok on 2009-12-01
I think I found the problem...
The use of % in the date command is conflicting with cron. Maybe its part of the crontab file syntax, I don't know for sure. But try removing that part and give a different name to the tar file. It should work now.

There should be a way to integrate the date feature too. One way I can think of is creating an alias for the `date '+%m%d%y'` in the user's .bashrc file and then calling that instead of the command in crontab. If you want to try this, do this. 
Open the file .bashrc in the user's folder and add this line:
```
alias getDate="date '+%m%d%y'"
```
Now, the tar command can be written like this:
```
tar pzcf /media/500/lucian_storage_backup/lucian_`getDate`.tgz /home/lucian/storage/*

```

Or you could also create a script with the one line **date '+%m%d%y'** and then place it in /usr/bin. Then you can call that script instead of getDate in the file crontab

This should work, but there should be a way to integrate that date command right in the crontab file. If we knew that, that would be more elegant maybe....

---

### Post by lmicu on 2009-12-01
Still won't work..... I tryed with the alias as well as with the script, the log indicates te script witch has 777 permisions.

root@server:/home/lucian# grep -i cron /var/log/syslog
Dec  1 06:52:01 server CRON[23322]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly ))
Dec  1 07:08:57 server crontab[23446]: (root) LIST (root)
Dec  1 07:09:21 server crontab[23452]: (root) LIST (root)
Dec  1 07:10:22 server crontab[23457]: (root) BEGIN EDIT (root)
Dec  1 07:10:39 server crontab[23457]: (root) REPLACE (root)
Dec  1 07:10:39 server crontab[23457]: (root) END EDIT (root)
Dec  1 07:10:41 server crontab[23463]: (root) LIST (root)
Dec  1 07:11:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:12:04 server crontab[23472]: (root) BEGIN EDIT (root)
Dec  1 07:12:21 server crontab[23472]: (root) REPLACE (root)
Dec  1 07:12:21 server crontab[23472]: (root) END EDIT (root)
Dec  1 07:12:24 server crontab[23478]: (root) LIST (root)
Dec  1 07:12:33 server crontab[23482]: (root) LIST (root)
Dec  1 07:12:39 server crontab[23485]: (root) BEGIN EDIT (root)
Dec  1 07:13:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:13:13 server crontab[23485]: (root) REPLACE (root)
Dec  1 07:13:13 server crontab[23485]: (root) END EDIT (root)
Dec  1 07:13:15 server crontab[23493]: (root) LIST (root)
Dec  1 07:14:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:14:01 server CRON[23499]: (root) CMD (echo luciy)
Dec  1 07:15:01 server CRON[23507]: (root) CMD (echo luciy)
Dec  1 07:15:05 server crontab[23510]: (root) BEGIN EDIT (root)
Dec  1 07:16:01 server CRON[23518]: (root) CMD (echo luciy)
Dec  1 07:16:32 server crontab[23510]: (root) REPLACE (root)
Dec  1 07:16:32 server crontab[23510]: (root) END EDIT (root)
Dec  1 07:17:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:17:01 server CRON[23529]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 07:17:01 server CRON[23531]: (root) CMD (echo luciy)
Dec  1 07:17:01 server CRON[23532]: (root) CMD (/usr/bin/tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 07:18:01 server CRON[23546]: (root) CMD (echo luciy)
Dec  1 07:18:42 server crontab[23558]: (root) LIST (root)
Dec  1 07:19:01 server CRON[23561]: (root) CMD (echo luciy)
Dec  1 07:20:01 server CRON[23571]: (root) CMD (echo luciy)
Dec  1 07:20:40 server crontab[23584]: (root) BEGIN EDIT (root)
Dec  1 07:21:01 server CRON[23590]: (root) CMD (echo luciy)
Dec  1 07:21:19 server crontab[23584]: (root) REPLACE (root)
Dec  1 07:21:19 server crontab[23584]: (root) END EDIT (root)
Dec  1 07:21:39 server crontab[23597]: (root) BEGIN EDIT (root)
Dec  1 07:21:48 server crontab[23597]: (root) REPLACE (root)
Dec  1 07:21:48 server crontab[23597]: (root) END EDIT (root)
Dec  1 07:22:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:22:01 server CRON[23608]: (root) CMD (pzcf /media/500/miriam_storage_backup/miriam_`getDate`.tgz /home/miriam/storage/* --report /etc/cron.weekly)
Dec  1 07:22:01 server CRON[23610]: (root) CMD (echo luciy)
Dec  1 07:22:11 server crontab[23619]: (root) BEGIN EDIT (root)
Dec  1 07:22:22 server crontab[23619]: (root) REPLACE (root)
Dec  1 07:22:22 server crontab[23619]: (root) END EDIT (root)
Dec  1 07:23:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:23:01 server CRON[23631]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_`getDate`.tgz /home/miriam/storage/* --report /etc/cron.weekly)
Dec  1 07:23:01 server CRON[23633]: (root) CMD (echo luciy)
Dec  1 07:23:30 server crontab[23655]: (root) BEGIN EDIT (root)
Dec  1 07:24:01 server CRON[23661]: (root) CMD (echo luciy)
Dec  1 07:24:02 server crontab[23655]: (root) REPLACE (root)
Dec  1 07:24:02 server crontab[23655]: (root) END EDIT (root)
Dec  1 07:24:08 server crontab[23667]: (root) BEGIN EDIT (root)
Dec  1 07:24:23 server crontab[23667]: (root) REPLACE (root)
Dec  1 07:24:23 server crontab[23667]: (root) END EDIT (root)
Dec  1 07:24:27 server crontab[23672]: (root) BEGIN EDIT (root)
Dec  1 07:24:50 server crontab[23672]: (root) REPLACE (root)
Dec  1 07:24:50 server crontab[23672]: (root) END EDIT (root)
Dec  1 07:25:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:25:01 server CRON[23681]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam.tgz /home/miriam/storage/*)
Dec  1 07:26:07 server crontab[23694]: (root) BEGIN EDIT (root)
Dec  1 07:26:35 server crontab[23694]: (root) REPLACE (root)
Dec  1 07:26:35 server crontab[23694]: (root) END EDIT (root)
Dec  1 07:26:35 server crontab[23700]: (root) BEGIN EDIT (root)
Dec  1 07:26:42 server crontab[23700]: (root) REPLACE (root)
Dec  1 07:26:42 server crontab[23700]: (root) END EDIT (root)
Dec  1 07:27:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:27:01 server CRON[23713]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_'getDate'.tgz /home/miriam/storage/*)
Dec  1 07:29:33 server crontab[23803]: (root) LIST (root)
Dec  1 07:31:56 server crontab[23813]: (root) BEGIN EDIT (root)
Dec  1 07:32:41 server crontab[23813]: (root) REPLACE (root)
Dec  1 07:32:41 server crontab[23813]: (root) END EDIT (root)
Dec  1 07:33:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:33:01 server CRON[23826]: (root) CMD (tar pzcf /usr/bin/getdate.sh)
Dec  1 07:33:20 server crontab[23841]: (root) LIST (root)
Dec  1 07:33:35 server crontab[23843]: (root) BEGIN EDIT (root)
Dec  1 07:33:41 server crontab[23843]: (root) REPLACE (root)
Dec  1 07:33:41 server crontab[23843]: (root) END EDIT (root)
Dec  1 07:33:43 server crontab[23847]: (root) BEGIN EDIT (root)
Dec  1 07:33:49 server crontab[23847]: (root) REPLACE (root)
Dec  1 07:33:49 server crontab[23847]: (root) END EDIT (root)
Dec  1 07:34:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:34:01 server CRON[23856]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:35:04 server crontab[23886]: (root) BEGIN EDIT (root)
Dec  1 07:35:07 server crontab[23886]: (root) END EDIT (root)
Dec  1 07:36:08 server crontab[23895]: (root) BEGIN EDIT (root)
Dec  1 07:36:15 server crontab[23895]: (root) REPLACE (root)
Dec  1 07:36:15 server crontab[23895]: (root) END EDIT (root)
Dec  1 07:37:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:37:01 server CRON[23907]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:38:27 server crontab[23933]: (root) BEGIN EDIT (root)
Dec  1 07:38:32 server crontab[23933]: (root) REPLACE (root)
Dec  1 07:38:32 server crontab[23933]: (root) END EDIT (root)
Dec  1 07:39:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:39:01 server CRON[23944]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:39:39 server crontab[23964]: (root) BEGIN EDIT (root)
Dec  1 07:39:42 server crontab[23964]: (root) END EDIT (root)
Dec  1 07:42:23 server crontab[23992]: (root) BEGIN EDIT (root)
Dec  1 07:43:12 server crontab[23998]: (root) BEGIN EDIT (root)
Dec  1 07:43:17 server crontab[23998]: (root) REPLACE (root)
Dec  1 07:43:17 server crontab[23998]: (root) END EDIT (root)
Dec  1 07:43:24 server crontab[23992]: (root) END EDIT (root)
Dec  1 07:44:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:44:01 server CRON[24013]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:46:17 server crontab[24055]: (root) BEGIN EDIT (root)
Dec  1 07:46:52 server crontab[24055]: (root) END EDIT (root)
Dec  1 07:49:47 server crontab[24083]: (root) BEGIN EDIT (root)
Dec  1 07:49:56 server crontab[24083]: (root) REPLACE (root)
Dec  1 07:49:56 server crontab[24083]: (root) END EDIT (root)
Dec  1 07:50:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:50:01 server CRON[24090]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:51:48 server crontab[24111]: (root) BEGIN EDIT (root)
Dec  1 07:51:51 server crontab[24111]: (root) END EDIT (root)
Dec  1 07:52:40 server crontab[24123]: (root) BEGIN EDIT (root)
Dec  1 07:52:44 server crontab[24123]: (root) REPLACE (root)
Dec  1 07:52:44 server crontab[24123]: (root) END EDIT (root)
Dec  1 07:53:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:53:01 server CRON[24131]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:53:24 server crontab[24145]: (root) BEGIN EDIT (root)
Dec  1 07:53:34 server crontab[24145]: (root) END EDIT (root)
Dec  1 07:53:46 server crontab[24151]: (root) BEGIN EDIT (root)
Dec  1 07:53:52 server crontab[24151]: (root) REPLACE (root)
Dec  1 07:53:52 server crontab[24151]: (root) END EDIT (root)
Dec  1 07:54:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:54:01 server CRON[24162]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 08:02:02 server crontab[24272]: (root) BEGIN EDIT (root)
Dec  1 08:02:27 server crontab[24272]: (root) REPLACE (root)
Dec  1 08:02:27 server crontab[24272]: (root) END EDIT (root)
Dec  1 08:03:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 08:03:01 server CRON[24287]: (root) CMD (tar pzcf -C / usr/bin/./getdate.sh)
Dec  1 08:03:55 server crontab[24310]: (root) BEGIN EDIT (root)
Dec  1 08:04:05 server crontab[24310]: (root) REPLACE (root)
Dec  1 08:04:05 server crontab[24310]: (root) END EDIT (root)
Dec  1 08:04:52 server crontab[24318]: (root) BEGIN EDIT (root)
Dec  1 08:05:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 08:05:02 server CRON[24323]: (root) CMD (tar zcf -C / usr/bin/./getdate.sh)
Dec  1 08:05:02 server crontab[24318]: (root) END EDIT (root)

---

### Post by raktarok on 2009-12-01
Its working on my computer, I just checked. I have attached the script I used to get the date. Place it in /usr/bin/ and make sure that its executable.(after copying it to /usr/bin, do **sudo chmod 755 /usr/bin/date-get**)

I placed this line in /etc/crontab,and now,its creating the file every one minute:
```
*/1 * * * * anup tar pzcf /home/anup/Doc/lucian_`date-get.sh`.tgz /home/anup/Desktop/*

```

Change the path to yours, and after the time entries, also change the username. If you are using individual crontab file for the user, then you don't need to add the user part.

Try this and it should definitely work. Good luck!

---

### Post by lmicu on 2009-12-01
> **raktarok said:**
> Its working on my computer, I just checked. I have attached the script I used to get the date. Place it in /usr/bin/ and make sure that its executable.(after copying it to /usr/bin, do **sudo chmod 755 /usr/bin/date-get**)

I placed this line in /etc/crontab,and now,its creating the file every one minute:
```
*/1 * * * * anup tar pzcf /home/anup/Doc/lucian_`date-get.sh`.tgz /home/anup/Desktop/*

```

Change the path to yours, and after the time entries, also change the username. If you are using individual crontab file for the user, then you don't need to add the user part.

Try this and it should definitely work. Good luck!


how did you reload the crontab, I place it but I did not use the crontab -e to enter it, I just nano it in to the /etc/crontab file . And it is not working.

Code:

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )


*/1 * * * * root tar pzcf /media/500/miriam_storage_backup/miriam_`getdate.sh'.tgz /home/miriam/storage/*
#

It does not create anything what so ever. What am I missing, I am sure it here somewhere.

If it is working on your computer I am sure it is something on my, I am assuming that the syntax is working and it is good, but it must have to do with some settings.

---

### Post by raktarok on 2009-12-01
That's what I did too,I opened the file in vi and added the line. and you don't need to reload too. Check if the cron process is running, but you may have already done that..try this if you want to:
```
sudo service cron restart
```
at the moment, when you type date-get.sh in the terminal, can you get the date? 
And are the cron tasks recorded in the /var/log/syslog? Please post the output like you did earlier. 

This is kind of weird (and frustruating). It should have worked this time...

---

### Post by lmicu on 2009-12-01
I found this in the ConHowTo from Ubuntu Community

//// The "%" character is used as newline delimiter in cron commands. If you need to pass that character into a script, you need to escape it as "\%". ////

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) 

I still cant figure it out.

Keep in mind, I am running Ubuntu Server 9.10 (I am not sure if you are running the same version as me, or if this makes a difference)

 .... I almost hit CTRL+X to save what I wrote here .... :)))

---

### Post by lmicu on 2009-12-01
The script is working, I get the date when I enter it, the cron is running, and I did reload it.

I notice that if I remove the script out of the syntax it is working just fine.

I will post the output for syslog but keep in mind that I am using a file called "luci" in the /etc/cron.d/luci to run the crontabs, and it is working also as long as I dont include the script or at least the "%"

Dec  1 06:52:01 server CRON[23322]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly ))
Dec  1 07:08:57 server crontab[23446]: (root) LIST (root)
Dec  1 07:09:21 server crontab[23452]: (root) LIST (root)
Dec  1 07:10:22 server crontab[23457]: (root) BEGIN EDIT (root)
Dec  1 07:10:39 server crontab[23457]: (root) REPLACE (root)
Dec  1 07:10:39 server crontab[23457]: (root) END EDIT (root)
Dec  1 07:10:41 server crontab[23463]: (root) LIST (root)
Dec  1 07:11:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:12:04 server crontab[23472]: (root) BEGIN EDIT (root)
Dec  1 07:12:21 server crontab[23472]: (root) REPLACE (root)
Dec  1 07:12:21 server crontab[23472]: (root) END EDIT (root)
Dec  1 07:12:24 server crontab[23478]: (root) LIST (root)
Dec  1 07:12:33 server crontab[23482]: (root) LIST (root)
Dec  1 07:12:39 server crontab[23485]: (root) BEGIN EDIT (root)
Dec  1 07:13:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:13:13 server crontab[23485]: (root) REPLACE (root)
Dec  1 07:13:13 server crontab[23485]: (root) END EDIT (root)
Dec  1 07:13:15 server crontab[23493]: (root) LIST (root)
Dec  1 07:14:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:14:01 server CRON[23499]: (root) CMD (echo luciy)
Dec  1 07:15:01 server CRON[23507]: (root) CMD (echo luciy)
Dec  1 07:15:05 server crontab[23510]: (root) BEGIN EDIT (root)
Dec  1 07:16:01 server CRON[23518]: (root) CMD (echo luciy)
Dec  1 07:16:32 server crontab[23510]: (root) REPLACE (root)
Dec  1 07:16:32 server crontab[23510]: (root) END EDIT (root)
Dec  1 07:17:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:17:01 server CRON[23529]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 07:17:01 server CRON[23531]: (root) CMD (echo luciy)
Dec  1 07:17:01 server CRON[23532]: (root) CMD (/usr/bin/tar pzcf /media/500/miriam_storage_backup/miriam_`date '+)
Dec  1 07:18:01 server CRON[23546]: (root) CMD (echo luciy)
Dec  1 07:18:42 server crontab[23558]: (root) LIST (root)
Dec  1 07:19:01 server CRON[23561]: (root) CMD (echo luciy)
Dec  1 07:20:01 server CRON[23571]: (root) CMD (echo luciy)
Dec  1 07:20:40 server crontab[23584]: (root) BEGIN EDIT (root)
Dec  1 07:21:01 server CRON[23590]: (root) CMD (echo luciy)
Dec  1 07:21:19 server crontab[23584]: (root) REPLACE (root)
Dec  1 07:21:19 server crontab[23584]: (root) END EDIT (root)
Dec  1 07:21:39 server crontab[23597]: (root) BEGIN EDIT (root)
Dec  1 07:21:48 server crontab[23597]: (root) REPLACE (root)
Dec  1 07:21:48 server crontab[23597]: (root) END EDIT (root)
Dec  1 07:22:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:22:01 server CRON[23608]: (root) CMD (pzcf /media/500/miriam_storage_backup/miriam_`getDate`.tgz /home/miriam/storage/* --report /etc/cron.weekly)
Dec  1 07:22:01 server CRON[23610]: (root) CMD (echo luciy)
Dec  1 07:22:11 server crontab[23619]: (root) BEGIN EDIT (root)
Dec  1 07:22:22 server crontab[23619]: (root) REPLACE (root)
Dec  1 07:22:22 server crontab[23619]: (root) END EDIT (root)
Dec  1 07:23:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:23:01 server CRON[23631]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_`getDate`.tgz /home/miriam/storage/* --report /etc/cron.weekly)
Dec  1 07:23:01 server CRON[23633]: (root) CMD (echo luciy)
Dec  1 07:23:30 server crontab[23655]: (root) BEGIN EDIT (root)
Dec  1 07:24:01 server CRON[23661]: (root) CMD (echo luciy)
Dec  1 07:24:02 server crontab[23655]: (root) REPLACE (root)
Dec  1 07:24:02 server crontab[23655]: (root) END EDIT (root)
Dec  1 07:24:08 server crontab[23667]: (root) BEGIN EDIT (root)
Dec  1 07:24:23 server crontab[23667]: (root) REPLACE (root)
Dec  1 07:24:23 server crontab[23667]: (root) END EDIT (root)
Dec  1 07:24:27 server crontab[23672]: (root) BEGIN EDIT (root)
Dec  1 07:24:50 server crontab[23672]: (root) REPLACE (root)
Dec  1 07:24:50 server crontab[23672]: (root) END EDIT (root)
Dec  1 07:25:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:25:01 server CRON[23681]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam.tgz /home/miriam/storage/*)
Dec  1 07:26:07 server crontab[23694]: (root) BEGIN EDIT (root)
Dec  1 07:26:35 server crontab[23694]: (root) REPLACE (root)
Dec  1 07:26:35 server crontab[23694]: (root) END EDIT (root)
Dec  1 07:26:35 server crontab[23700]: (root) BEGIN EDIT (root)
Dec  1 07:26:42 server crontab[23700]: (root) REPLACE (root)
Dec  1 07:26:42 server crontab[23700]: (root) END EDIT (root)
Dec  1 07:27:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:27:01 server CRON[23713]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_'getDate'.tgz /home/miriam/storage/*)
Dec  1 07:29:33 server crontab[23803]: (root) LIST (root)
Dec  1 07:31:56 server crontab[23813]: (root) BEGIN EDIT (root)
Dec  1 07:32:41 server crontab[23813]: (root) REPLACE (root)
Dec  1 07:32:41 server crontab[23813]: (root) END EDIT (root)
Dec  1 07:33:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:33:01 server CRON[23826]: (root) CMD (tar pzcf /usr/bin/getdate.sh)
Dec  1 07:33:20 server crontab[23841]: (root) LIST (root)
Dec  1 07:33:35 server crontab[23843]: (root) BEGIN EDIT (root)
Dec  1 07:33:41 server crontab[23843]: (root) REPLACE (root)
Dec  1 07:33:41 server crontab[23843]: (root) END EDIT (root)
Dec  1 07:33:43 server crontab[23847]: (root) BEGIN EDIT (root)
Dec  1 07:33:49 server crontab[23847]: (root) REPLACE (root)
Dec  1 07:33:49 server crontab[23847]: (root) END EDIT (root)
Dec  1 07:34:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:34:01 server CRON[23856]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:35:04 server crontab[23886]: (root) BEGIN EDIT (root)
Dec  1 07:35:07 server crontab[23886]: (root) END EDIT (root)
Dec  1 07:36:08 server crontab[23895]: (root) BEGIN EDIT (root)
Dec  1 07:36:15 server crontab[23895]: (root) REPLACE (root)
Dec  1 07:36:15 server crontab[23895]: (root) END EDIT (root)
Dec  1 07:37:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:37:01 server CRON[23907]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:38:27 server crontab[23933]: (root) BEGIN EDIT (root)
Dec  1 07:38:32 server crontab[23933]: (root) REPLACE (root)
Dec  1 07:38:32 server crontab[23933]: (root) END EDIT (root)
Dec  1 07:39:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:39:01 server CRON[23944]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:39:39 server crontab[23964]: (root) BEGIN EDIT (root)
Dec  1 07:39:42 server crontab[23964]: (root) END EDIT (root)
Dec  1 07:42:23 server crontab[23992]: (root) BEGIN EDIT (root)
Dec  1 07:43:12 server crontab[23998]: (root) BEGIN EDIT (root)
Dec  1 07:43:17 server crontab[23998]: (root) REPLACE (root)
Dec  1 07:43:17 server crontab[23998]: (root) END EDIT (root)
Dec  1 07:43:24 server crontab[23992]: (root) END EDIT (root)
Dec  1 07:44:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:44:01 server CRON[24013]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:46:17 server crontab[24055]: (root) BEGIN EDIT (root)
Dec  1 07:46:52 server crontab[24055]: (root) END EDIT (root)
Dec  1 07:49:47 server crontab[24083]: (root) BEGIN EDIT (root)
Dec  1 07:49:56 server crontab[24083]: (root) REPLACE (root)
Dec  1 07:49:56 server crontab[24083]: (root) END EDIT (root)
Dec  1 07:50:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:50:01 server CRON[24090]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:51:48 server crontab[24111]: (root) BEGIN EDIT (root)
Dec  1 07:51:51 server crontab[24111]: (root) END EDIT (root)
Dec  1 07:52:40 server crontab[24123]: (root) BEGIN EDIT (root)
Dec  1 07:52:44 server crontab[24123]: (root) REPLACE (root)
Dec  1 07:52:44 server crontab[24123]: (root) END EDIT (root)
Dec  1 07:53:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:53:01 server CRON[24131]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 07:53:24 server crontab[24145]: (root) BEGIN EDIT (root)
Dec  1 07:53:34 server crontab[24145]: (root) END EDIT (root)
Dec  1 07:53:46 server crontab[24151]: (root) BEGIN EDIT (root)
Dec  1 07:53:52 server crontab[24151]: (root) REPLACE (root)
Dec  1 07:53:52 server crontab[24151]: (root) END EDIT (root)
Dec  1 07:54:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 07:54:01 server CRON[24162]: (root) CMD (tar pzcf /usr/bin/./getdate.sh)
Dec  1 08:02:02 server crontab[24272]: (root) BEGIN EDIT (root)
Dec  1 08:02:27 server crontab[24272]: (root) REPLACE (root)
Dec  1 08:02:27 server crontab[24272]: (root) END EDIT (root)
Dec  1 08:03:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 08:03:01 server CRON[24287]: (root) CMD (tar pzcf -C / usr/bin/./getdate.sh)
Dec  1 08:03:55 server crontab[24310]: (root) BEGIN EDIT (root)
Dec  1 08:04:05 server crontab[24310]: (root) REPLACE (root)
Dec  1 08:04:05 server crontab[24310]: (root) END EDIT (root)
Dec  1 08:04:52 server crontab[24318]: (root) BEGIN EDIT (root)
Dec  1 08:05:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 08:05:02 server CRON[24323]: (root) CMD (tar zcf -C / usr/bin/./getdate.sh)
Dec  1 08:05:02 server crontab[24318]: (root) END EDIT (root)
Dec  1 08:17:02 server CRON[24495]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 09:17:02 server CRON[24679]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 10:17:03 server CRON[24869]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 11:17:02 server CRON[25055]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 12:17:03 server CRON[25242]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 13:17:02 server CRON[25427]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 14:17:01 server CRON[25614]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 15:17:01 server CRON[25799]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 16:17:01 server CRON[25986]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 17:17:01 server CRON[26169]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 18:17:01 server CRON[26353]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 19:16:40 server crontab[26678]: (root) BEGIN EDIT (root)
Dec  1 19:17:01 server CRON[26684]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  1 19:18:39 server crontab[26678]: (root) REPLACE (root)
Dec  1 19:18:39 server crontab[26678]: (root) END EDIT (root)
Dec  1 19:18:50 server crontab[26692]: (root) BEGIN EDIT (root)
Dec  1 19:19:01 server cron[1077]: (root) RELOAD (crontabs/root)
Dec  1 19:19:07 server crontab[26692]: (root) END EDIT (root)
Dec  1 19:20:01 server CRON[26701]: (root) CMD (tar pzcf /media/500/miriam_storage_backup/miriam_'getdate.sh'.tgz /home/miriam/storage/*)
Dec  1 19:20:02 server CRON[26700]: (root) MAIL (mailed 168 bytes of output but got status 0x0001#012)
Dec  1 19:21:05 server crontab[26714]: (root) LIST (root)
Dec  1 19:21:12 server crontab[26716]: (root) BEGIN EDIT (root)
Dec  1 19:21:19 server crontab[26716]: (root) REPLACE (root)
Dec  1 19:21:19 server crontab[26716]: (root) END EDIT (root)
Dec  1 19:21:22 server crontab[26720]: (root) LIST (root)
Dec  1 19:21:43 server crontab[26723]: (root) LIST (root)
Dec  1 19:22:01 server cron[1077]: (root) RELOAD Dec  1 19:47:18 server rsyslogd: connot create '/var/spool/postfix/dev/log': No such file or directory

---

### Post by raktarok on 2009-12-01
Your command has this part and I think this is the problem:
```
miriam_'getdate.sh'.tgz 
```
Instead, it should be this:
```
miriam_`getdate.sh`.tgz 
```
Look closely at the quotes, you will see. :)
The **`** should be below the tilda(~) in your keyboard. By using this sign here, we are using the output of the command. The single quote character(') does not do that at all.

Anyway, you found the better solution. So the part:
```
lucian_`date '+%m%d%y'`.tgz
```
would be this.
```
lucian_`date '+\%m\%d\%y'`.tgz
```
Try this, this is certainly better, and take care of the quotes!

Edit: I tried the second format, and it certainly works!

---

### Post by lmicu on 2009-12-01
:) BINGO

echo BINGO

BINGO

it is working

this is the sollution:

lucian_`date '+\%m\%d\%y'`.tgz 

instead of

lucian_`date '+%m%d%y'`.tgz

Man, thanks lots, I killed 2 nights over this. I guess I should keep and closer eye on to the howto's.

Good Night

---

### Post by lmicu on 2009-12-01
one more question:

how come it was working in the initial stage on your computer, what verion and distro are you using?

---

### Post by raktarok on 2009-12-01
Glad to hear that..and good night from me too!

By initial stage, do you mean when I used the script? I have pointed out your error regarding that in the above post, I think.  
and I am using ubuntu karmic. 
oh I see now what verion is haha..:)

---

