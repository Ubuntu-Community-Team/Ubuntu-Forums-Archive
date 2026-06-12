---
title: "Permissions on mail box?"
date: 2010-06-03
forum: General Help
---

### Post by jerome1232 on 2010-06-03
So mail wasn't setup during installation for some reason on my box. So I installed postfix and mailutils, ran them through the config, now when I try and check my mail I get...

```
jeremy@voiceserv:~$ mail
Cannot open mailbox /var/mail/jeremy: Permission denied
No mail for jeremy
```

The permissions are

```
jeremy@voiceserv:~$ ls -l /var/mail/jeremy 
-rw------- 1 root mail 0 2010-06-03 13:36 /var/mail/jeremy

```


My groups are
```
jeremy@voiceserv:~$ groups
jeremy adm dialout cdrom plugdev lpadmin sambashare admin

```

So my question is what is wrong here?

---

### Post by kuhkatz on 2010-06-05
found this thread by seaching for the same problem.

difference on my system: /var/mail/<username> didnt even exist.

```

sudo touch /var/mail/<username>
sudo chown <username>:mail /var/mail/<username>
sudo chmod o-r /var/mail/<username>
sudo chmod g+rw /var/mail/<username>

```seemed to fix the issue - at least the error is gone.
dunno if this is how it will work, thou.

---

### Post by jerome1232 on 2010-06-05
Okay well that makes sence at least, although I made the permissions a little more restrictive (actually left them more restrictive) 

After making changes I sent a test mail to my own user and it worked, whereas before I wasn't getting mail at all.

I simply changed the owner of /var/mail/<username> from root:mail to <username>:mail, left the permissions -rw-------


```
jeremy@voiceserv:~$ sudo chmod jeremy:mail /var/mail/jeremy
[sudo] password for jeremy:
jeremy@voiceserv:~$ ls -l /var/mail/jeremy 
-rw------- 1 jeremy mail 0 2010-06-03 13:36 /var/mail/jeremy
jeremy@voiceserv:~$ mail jeremy@voiceserv.homelinux.net
Cc: 
Subject: test
testing123
jeremy@voiceserv:~$ mail
"/var/mail/jeremy": 1 message 1 new
>N   1 Jeremy DeBry Jones Sat Jun  5 09:26  13/516   test
? 1
Return-Path: <jeremy@voiceserv.homelinux.net>
X-Original-To: jeremy@voiceserv.homelinux.net
Delivered-To: jeremy@voiceserv.homelinux.net
Received: by voiceserv.homelinux.net (Postfix, from userid 1000)
	id 263CC9E5; Sat,  5 Jun 2010 09:26:31 -0700 (PDT)
To: <jeremy@voiceserv.homelinux.net>
Subject: test
X-Mailer: mail (GNU Mailutils 2.1)
Message-Id: <20100605162631.263CC9E5@voiceserv.homelinux.net>
Date: Sat,  5 Jun 2010 09:26:31 -0700 (PDT)
From: jeremy@voiceserv.homelinux.net (Jeremy DeBry Jones)

testing123
? q
Saved 1 message in /home/jeremy/mbox
Held 0 messages in /var/mail/jeremy
```

---

### Post by codeninja1 on 2011-02-18
A minor improvement on khukatz's code to reduce the chance for typos

```
sudo touch /var/mail/$USER
sudo chown $USER:mail /var/mail/$USER
sudo chmod o-r /var/mail/$USER
sudo chmod g+rw /var/mail/$USER
```

---

