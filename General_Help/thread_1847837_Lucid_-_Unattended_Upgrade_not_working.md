---
title: "Lucid - Unattended Upgrade not working"
date: 2011-09-21
forum: General Help
---

### Post by windyweather on 2011-09-21
I'm trying to set my systems up for unattended upgrade using this page:
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

the Natty system works fine, based on the logs I've found.
But the Lucid system is having problems. See below. I found this in the /var/mail file. I don't yet have the mail working to send the mail out, but at least here it is.

Looks like the unattended upgrade steps were not run. Of course the logrotate steps failed after that since this is the first time.
I have checked that the cron.daily/apt-security-updates file is set to exec. Also see that file below.

Oddly enough, the natty system appears to have run, but via some other mechanism,since there is no log created by this script, but it shows an apt history log that shows it ran. Strange, but another question.

Thanks,
- ww

Mail showing it failed:
```
From root@squall-ubuntu Wed Sep 21 07:40:56 2011
Return-path: <root@squall-ubuntu>
Envelope-to: root@squall-ubuntu
Delivery-date: Wed, 21 Sep 2011 07:40:56 -0700
Received: from root by squall-ubuntu with local (Exim 4.71)
	(envelope-from <root@squall-ubuntu>)
	id 1R6Nyq-0000Sk-6j
	for root@squall-ubuntu; Wed, 21 Sep 2011 07:40:56 -0700
Date: Wed, 21 Sep 2011 07:40:56 -0700
Message-Id: <E1R6Nyq-0000Sk-6j@squall-ubuntu>
From: Anacron <root@squall-ubuntu>
To: root@squall-ubuntu
Subject: Anacron job 'cron.daily' on squall-ubuntu

/etc/cron.daily/apt:
verbose level 1
power status (255) undetermined, continuing
system is on main power.
sleeping for 336 seconds
download updated metadata (not run).
download upgradable (not run)
unattended-upgrade (not run)
check_stamp: missing time stamp file: /var/lib/apt/periodic/autoclean-stamp.
autoclean (success).
aged: ctime <30 and mtime <30 and ctime>2 and mtime>2
end remove by archive size: size=178896 < 512000
/etc/cron.daily/apt-security-updates:
run-parts: failed to exec /etc/cron.daily/apt-security-updates: Exec format error
run-parts: /etc/cron.daily/apt-security-updates exited with return code 1
/etc/cron.daily/logrotate:
error: stat of /var/log/apt-security-updates failed: No such file or directory
run-parts: /etc/cron.daily/logrotate exited with return code 1

```

apt-security-updates file:
```
echo "**************" >> /var/log/apt-security-updates
date >> /var/log/apt-security-updates
aptitude update >> /var/log/apt-security-updates
aptitude safe-upgrade -o Aptitude::Delete-Unused=false --assume-yes --target-release `lsb_release -cs`-security >> /var/log/apt-security-updates
echo "Security updates (if any) installed"
```

---

### Post by dcstar on 2011-09-22
> **windyweather said:**
> I'm trying to set my systems up for unattended upgrade using this page:
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

the Natty system works fine, based on the logs I've found.
But the Lucid system is having problems.
........

The last edit date on that page show that is written well before 11.04 was released, so it is safe to assume that it only has been tested to work with 10.10 and it seems strange that the later one works for you.

---

### Post by windyweather on 2011-09-22
Ok... But it does work on Natty. So maybe that's why the cron stuff doesn't seem to be working, but the unattended update seems to be working anyway.

So the page should work for 10.04, and doesn't apparently? Or was it instructions for 10.10, not 10.04? Any pointers to instructions for 10.04? I don't see any place on the page it mentions what versions it is describing.

<< Crickets.. .Crickets... >> Anybody out there that knows how this stuff works??

Thanks,
ww

---

