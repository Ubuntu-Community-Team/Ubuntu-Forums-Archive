---
title: "warning after update"
date: 2010-03-18
forum: General Help
---

### Post by adeelm on 2010-03-18
hi,

     I am using ubuntu 9.10 and I updated by ubuntu machine. It updated but at the end it gave me a message that "You have new mail in /var/mail/root".

when I checked it via the command "tail /var/mail/root" it showed me this.

 tail /var/mail/root
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Message-Id: <20100318051502.0D1ABB1C01@Infosec-Lab04>
Date: Thu, 18 Mar 2010 10:15:02 +0500 (PKT)

WARNING: "MaxBytes[leased]" not specified
ERROR: Please fix the error(s) in your config file

 please help me understand what does this warning means and which  configuration file it refers to.

Thanks
Adeel

---

### Post by wjm on 2010-03-18
That is a warning about mrtg or "multiple router traffic grapher".  Specifically it is referring to the "MaxBytes" variable in the mrtg configuration file.  It is probably sending that mail out to complain to you about it not being set -- thus your graphs will be inconsistent (to say the very least)

---

