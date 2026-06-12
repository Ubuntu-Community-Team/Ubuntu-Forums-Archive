---
title: "Postfix Error"
date: 2011-06-02
forum: General Help
---

### Post by Jay89 on 2011-06-02
Hello, I have a ubuntu 10.0.4 email server using Postfix and Dovecot. Dovecot is configured (successfully I hope) for SSL authentication. I _can_ connect to it from thunderbird fine (I assume as I see no errors in /var/log or thunderbird to tell me otherwise). Up until I configured it to use SSL I have been able to at least send email to the _local_ accounts through the command line via mail-s and telnet. But now I am getting this error and the messages don't reach the inbox. Any Suggestions?

Thanks!!!

Jun  2 12:55:47 newmail postfix/cleanup[2095]: 5A55A19C1DE0: message-id=<20110602165547.5A55A19C1DE0@newmail.testdegc.net>
Jun  2 12:55:47 newmail postfix/qmgr[1898]: 5A55A19C1DE0: from=<root@newmail.testdegc.net>, size=343, nrcpt=1 (queue active)
Jun  2 12:55:47 newmail postfix/local[2097]: warning: database /etc/aliases.db is older than source file /etc/aliases
**Jun  2 12:55:47 newmail postfix/local[2097]: 5A55A19C1DE0: to=<testit@newmail.testdegc.net>, orig_to=<testit@localhost>, relay=local, delay=0.31, delays=0.12/0.06/0/0.12, dsn=5.2.0, status=bounced (cannot update mailbox /home/testit/.maildir for user testit. cannot open file: Is a directory)**
Jun  2 12:55:47 newmail postfix/cleanup[2095]: 981EB19C1DE3: message-id=<20110602165547.981EB19C1DE3@newmail.testdegc.net>
Jun  2 12:55:47 newmail postfix/bounce[2098]: 5A55A19C1DE0: sender non-delivery notification: 981EB19C1DE3
Jun  2 12:55:47 newmail postfix/qmgr[1898]: 981EB19C1DE3: from=<>, size=2395, nrcpt=1 (queue active)
Jun  2 12:55:47 newmail postfix/qmgr[1898]: 5A55A19C1DE0: removed
**Jun  2 12:55:47 newmail postfix/local[2097]: 981EB19C1DE3: to=<root@newmail.testdegc.net>, relay=local, delay=0.13, delays=0.07/0/0/0.07, dsn=5.2.0, status=bounced (cannot update mailbox /root/.maildir for user root. cannot open file: Is a directory)**
Jun  2 12:55:47 newmail postfix/qmgr[1898]: 981EB19C1DE3: removed

---

### Post by Jay89 on 2011-06-03
Found the solution, at least for me anyway. I had to do an **apt-get install dovecot-postfix**. Once it configured itself, I was able to to do a **mail -s to testit@localhost**.

---

