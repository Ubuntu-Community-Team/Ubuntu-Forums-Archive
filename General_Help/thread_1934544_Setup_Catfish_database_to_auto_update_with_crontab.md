---
title: "Setup Catfish database to auto update with crontab"
date: 2012-03-02
forum: General Help
---

### Post by Rytron on 2012-03-02
Hi.
I just want confirmation with setting up the Catfish database to automatically update with crontab. Is the following correct? "**0 9 * * * root sudo updatedb**". Or must I change "root" to my username?
Thanks.

```
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
0 9 * * * root sudo updatedb
```

---

### Post by hwttdz on 2012-03-02
If you were logged in as your user what would the comand that you would run at terminal be?
And if you were logged in as root?

It might be easier to just put the command in the crontab for your user if it needs to run as your user, or in root's crontab if you need it to run as root.

---

### Post by Rytron on 2012-03-03
> **hwttdz said:**
> If you were logged in as your user what would the comand that you would run at terminal be?

Hi hwttdz.

```
sudo updatedb
```

> **hwttdz said:**
> And if you were logged in as root?

I'd pretty much never be logged in as root.

---

### Post by hwttdz on 2012-03-05
In that case the command is running as root.  So I'd put it in the root users crontab.  

```
sudo -i
crontab -e
```

and then add the line
"0 9 * * * updatedb"
it will be run as the root user (with the corresponding permissions).  You could also give your user rights to run that command as root without a password via editing the sudoers file, but this keeps segregation of the root account and user account.  This should not introduce any new security issues.

---

### Post by Rytron on 2012-03-05
> **hwttdz said:**
> In that case the command is running as root.  So I'd put it in the root users crontab.  

```
sudo -i
crontab -e
```

and then add the line
"0 9 * * * updatedb"
it will be run as the root user (with the corresponding permissions).  You could also give your user rights to run that command as root without a password via editing the sudoers file, but this keeps segregation of the root account and user account.  This should not introduce any new security issues.

Cheers hwttdz.

---

### Post by Rytron on 2012-04-18
```
42 * * * * root updatedb
```

---

