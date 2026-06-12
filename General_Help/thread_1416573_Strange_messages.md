---
title: "Strange messages"
date: 2010-02-26
forum: General Help
---

### Post by spandey on 2010-02-26
Hi,
I am new to Linux. So please bear with me. My syslog is full of these messages. They keep appearing. Any idea what it is.

Feb 26 19:28:15 spandey-desktop postfix/pickup[2511]: fatal: match_list_parse: open file /etc/mailname: No such file or directory
Feb 26 19:28:15 spandey-desktop postfix/qmgr[2512]: fatal: match_list_parse: open file /etc/mailname: No such file or directory
Feb 26 19:28:16 spandey-desktop postfix/master[1417]: warning: process /usr/lib/postfix/pickup pid 2511 exit status 1
Feb 26 19:28:16 spandey-desktop postfix/master[1417]: warning: /usr/lib/postfix/pickup: bad command startup -- throttling
Feb 26 19:28:16 spandey-desktop postfix/master[1417]: warning: process /usr/lib/postfix/qmgr pid 2512 exit status 1
Feb 26 19:28:16 spandey-desktop postfix/master[1417]: warning: /usr/lib/postfix/qmgr: bad command startup -- throttling

---

### Post by julipanno on 2010-02-26
First of all, are you sure you need Postfix running on your desktop computer?

Postfix is a complex MTA (Mail Transport Agent), and if you don't intend to run your own mail server, you probably don't need it.

It can be removed by issuing the command
```
sudo aptitude purge postfix
```

If, however, you *do* need to have postfix running, I recommend taking some time getting familiar with the config files
/etc/postfix/main.cf
/etc/postfix/master.cf
You should also read the [Postfix documentation]("http://www.postfix.org/documentation.html"), making sure you understand what every line in the config files do. A wrongly configured MTA can easily make your computer a tool for spammers.

---

### Post by spandey on 2010-02-26
Thanks a lot Julipanno. I don't need it. Does it come with Ubuntu default?

I am having lots of problem with PPPoe.  Can you point me to configuration files and steps in PPP0e connection so that I can try to figure out what my problems are?

---

### Post by julipanno on 2010-02-26
> **spandey said:**
> Thanks a lot Julipanno. I don't need it. Does it come with Ubuntu default?
Fortunately not ;-)
If you didn't install it on purpose, it might have been pulled in as a dependency for something else.

> **spandey said:**
> I am having lots of problem with PPPoe.  Can you point me to configuration files and steps in PPP0e connection so that I can try to figure out what my problems are?
I have hardly used PPPoe, so I don't know how it should be configured, but its config files can be found in /etc/ppp/

---

### Post by spandey on 2010-02-26
I uninstalled and messagea re gone

---

