---
title: "I want to remove a cron.d entry"
date: 2006-02-28
forum: General Help
---

### Post by Mustard on 2006-02-28
I had sbackup installed, but recently removed it.  I used the --purge option to remove config files, but it seems I have a remnant of the installation on my system.  I'm getting this message from Cron Daemon.

(NOTE:- I had installed the latest sbackup using checkinstall to create a .deb package so I could uninstall via synaptic.  This is not the sbackup version found in the standard repositories.)

```
From: Cron Daemon <root@localhost.localdomain>
To: root@localhost.localdomain
Subject: Cron <root@slave> /usr/sbin/sbackupd
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>

/bin/sh: /usr/sbin/sbackupd: No such file or directory

```

Looking in /etc/cron.d/ I find this

```
mustard@slave:/etc/cron.d$ ls
anacron  sbackup  tiger
mustard@slave:/etc/cron.d$ cat sbackup
@daily  root    /usr/sbin/sbackupd

```

What is the appropriate way to go about removing this manually? Do I just delete the sbackup file in /etc/cron.d/ ?

---

### Post by DonVla on 2006-02-28
hello,

yes. cron reads out the files in /etc/cron.d/ . if there is a cronjob you don't want you can simply remove that file.

vlad

---

### Post by Mustard on 2006-02-28
Thanks for the quick help. :)

Thats one less message I need to read from the system now..hehe..

---

