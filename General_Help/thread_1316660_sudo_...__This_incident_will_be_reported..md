---
title: "sudo: ...  This incident will be reported."
date: 2009-11-06
forum: General Help
---

### Post by Wim Sturkenboom on 2009-11-06
```

fortyfourgalena@desktop1:~$ sudo fdisk -l
[sudo] password for fortyfourgalena: 
fortyfourgalena is not in the sudoers file.  **This incident will be reported.**
fortyfourgalena@desktop1:~$

```Where? In Slackware a mail is send to the root user. However I don't know where to look for it in Ubuntu. As the mail package is not installed by default, it does not make sense that it's mailed.

PS OS is 8.04, in case it matters

---

### Post by ghostborg on 2009-11-06
Try this thread.

[http://ubuntuforums.org/showthread.php?t=65815]("http://ubuntuforums.org/showthread.php?t=65815"):lolflag:



Opps! I posted this to the wrong thread. Sorry!

---

### Post by AlphaLexman on 2009-11-06
I agree with the OP's logic, but what you're looking for might be:

```
sudo apt-get install mail
```

or in the folder /var/mail/

---

### Post by t0p on 2009-11-06
> **ghostborg said:**
> Try this thread.

[http://ubuntuforums.org/showthread.php?t=65815](http://ubuntuforums.org/showthread.php?t=65815):lolflag:

ghostborg: did you read the opening post?  That link has got nothing to do with the OP's question.

OP: I'd also like to know the answer to your question.  I just carried out an experiment: I logged in as a non-sudoer, tried to run the sudo command, and got the same dire warning: "This incodent will be reported".  Then I logged in as root and checked the system mail (mailx is installed on this machine).  But there was no mail reporting the incident to me.

I'm gonna have a poke around as root, see if the report is somewhere else.  I'll report back any findings.

**EDIT:** I found it!!!  I logged into my usual user account (the one that I created when I installed Hardy on this machine) and checked my mail - and there it was!

```

t0p@phobos:~$ mail
Mail version 8.1.2 01/15/2001.  Type ? for help.
"/var/mail/t0p": 3 messages 3 new
>N  1 newsletter@blogcr  Fri Nov 06 11:00  553/27689 BC/Technorati Newsletter #2
 N  2 ubuntu-uk-request  Fri Nov 06 11:00  511/17165 ubuntu-uk Digest, Vol 55, I
 N  3 piratex@phobos     Fri Nov 06 12:26   18/644   *** SECURITY information fo
& 3
Message 3:
From piratex@phobos Fri Nov 06 12:26:31 2009
Envelope-to: root@phobos
Delivery-date: Fri, 06 Nov 2009 12:26:31 +0000
To: root@phobos
Auto-Submitted: auto-generated
Subject: *** SECURITY information for phobos ***
From: Long John Silver <piratex@phobos>
Date: Fri, 06 Nov 2009 12:26:30 +0000

phobos : Nov  6 12:26:29 : piratex : user NOT in sudoers ; TTY=tty1 ; PWD=/home/piratex ; USER=root ; COMMAND=/bin/bash

```

So there you go.  Install a system mail program (mailx is the one I installed) and the report is sent to your main user's mailbox.

---

### Post by hal10000 on 2009-11-06
I guess such things will be logged to /var/log/messages or to one of the other logfiles in /var/log

---

### Post by Wim Sturkenboom on 2009-11-10
Thanks for the replies and sorry for the late feedback.

Nothing to be found unless I'm blind. I ran a *grep -R* on my (admin's) home directory, on root's home directory and on /var/log .

I understand that I can install the mail package but that's beside the point. If it says that it will be reported, it should be reported or it should keep its mouth shut.

If somebody else has a clever idea or a different experience, please let me know.

---

### Post by sisco311 on 2009-11-10
it's logged to /var/log/auth.log:
```
grep "user NOT in sudoers" /var/log/auth.log
```

---

### Post by Wim Sturkenboom on 2009-11-10
Thanks, I should have used better search criteria with grep ](*,)

---

