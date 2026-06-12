---
title: "Syslog - /etc/postfix/main.cf: No such file or directory"
date: 2010-05-23
forum: General Help
---

### Post by HotForLinux on 2010-05-23
Every hour, when cron does  a user programmed job that basically executes the following:

> sudo /usr/sbin/ntpdate ntp.ubuntu.com  europe.pool.ntp.org


 syslog is logging the following message:

```

May 23 19:57:02 hostname postfix/sendmail[11452]: fatal: open /etc/postfix/main.cf: No such file or directory
```And it is true: main.cf does not exist. There's a file called master.cf, instead.

Any idea about what is going on?
Sendamil is not installed, evolution was recently cleaned up deleting all the mails.

```
dpkg -l *mail* |grep "^ii"
ii  egroupware-emailadmin                      1.2.107-2.dfsg-2ubuntu1                                    eGroupWare E-mail user administration applic
ii  egroupware-felamimail                      1.2.107-2.dfsg-2ubuntu1                                    eGroupWare FeLaMiMail application
ii  kmail                                      4:3.5.10-0ubuntu1~hardy3.2                                 KDE Email client
ii  kmailcvt                                   4:3.5.10-0ubuntu1~hardy3.2                                 KDE KMail mail folder converter
```

---

### Post by Rod J on 2010-06-12
I'd like to know what the cause of this error message in the syslog is too. I'm seeing it in relation to a cron backup job. Maybe it's not a problem, I don't know.

---

### Post by chenxiaolong on 2010-06-12
Are you sure you have postfix installed?

If you do, try reinstalling it with:

```
sudo apt-get install --reinstall postfix
```

then run:

```
sudo dpkg-reconfigure postfix
```

It should give you an information screen, just press OK. On the next screen (**General type of mail configuration**), choose **Local only**. Just press Enter when it asks you for the System mail name. Also press Enter when it asks for the "Root and postmaster email recipient." And enter on the "Other destinations to accept mail for" screen (getting repetitive, isn't it :D). Choose No for the "Force synchronous updates on mail queue" screen. And just press Enter for the rest of the screens.

That should create the /etc/postfix/mail.cf file for you.

Hopefully that'll work :D.

---

### Post by Rod J on 2010-06-13
Thanks chenxiaolong, that fixed it. But, I'm not sure I want postfix running all the time just to stop that trivial error message appearing.

---

### Post by chenxiaolong on 2010-06-13
You can yus BUM (Ubuntu BootUp Manager) to turn off the postfix service from running at boot (and any other services).

```
sudo apt-get install bum
sudo bum
```

---

### Post by HotForLinux on 2011-06-04
Oh, I have just done it and after reconfiguring postfix to work for a local machine, as you said, the incessant logging seems to have stopped.

But I  don't understand.
-Why wasn't postfix configured or was not configures as a local service?
-Why is postfix now working as a daemon and not before?
-What do I need it for in a normal desktop install?
- Is it safe to disable the service in the runlevel scritps (rc.d's)?

---

