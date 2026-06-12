---
title: "cron does not write hostname on the sender address"
date: 2009-11-18
forum: General Help
---

### Post by supremedalek on 2009-11-18
Right now, all the emails I am getting from cron have the following From: field:

```
From: Cron Daemon <root>
```

How can I have it write the FQDN of the host, as in

```
From: Cron Daemon <root@machine.domain.com>
```

---

### Post by falconindy on 2009-11-18
This isn't because of cron, it's because of whatever mailing daemon you're using.

---

### Post by supremedalek on 2009-11-23
I see. I wrote a little script to make a copy of what is being passed to ssmtp. Here is the output from my test cron job:

```
From: root (Cron Daemon)
To: raub@domain.com
Subject: Cron <root@desktop>    /root/scripts/df.sh
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/bash>
X-Cron-Env: <PATH=/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/>
X-Cron-Env: <MAILTO=raub@domain.com>
X-Cron-Env: <LOGNAME=root>

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/root
                      576G  303G  245G  56% /
tmpfs                 3.9G     0  3.9G   0% /lib/init/rw
varrun                3.9G  260K  3.9G   1% /var/run
varlock               3.9G     0  3.9G   0% /var/lock
udev                  3.9G  160K  3.9G   1% /dev
tmpfs                 3.9G  908K  3.9G   1% /dev/shm
lrm                   3.9G  2.5M  3.9G   1%
/lib/modules/2.6.28-16-generic/volatile
/dev/sda5             228M   71M  145M  33% /boot
```

---

