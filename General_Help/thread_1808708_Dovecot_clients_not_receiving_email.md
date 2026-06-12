---
title: "Dovecot clients not receiving email"
date: 2011-07-20
forum: General Help
---

### Post by lordbah on 2011-07-20
I've had this setup working but today it suddenly stopped. Ubuntu 11.04 running dovecot. My phone and tablet both stopped receiving new emails. I've restarted dovecot (and the devices) a number of times, but no help. It seems like they are logging in successfully, they simply aren't retrieving any new emails. No error appears on the clients. I can read old emails, and I can download attachments from old emails. It's just that I don't get any new emails. Any idea what to look for?


Jul 20 16:52:34 penguin dovecot: auth(default): new auth connection: pid=3624
Jul 20 16:52:34 penguin dovecot: auth(default): client in: AUTH#0111#011PLAIN#011service=imap#011secured#011lip=192.168.218.119#011rip=<ip>#011lport=993#011rport=48219#011resp=<hidden>
Jul 20 16:52:34 penguin dovecot: auth-worker(default): pam(mobile,<ip>): lookup service=dovecot
Jul 20 16:52:34 penguin dovecot: auth-worker(default): pam(mobile,<ip>): #1/1 style=1 msg=Password:
Jul 20 16:52:34 penguin dovecot: auth(default): client out: OK#0111#011user=mobile
Jul 20 16:52:34 penguin dovecot: auth(default): master in: REQUEST#0118#0113570#0111
Jul 20 16:52:34 penguin dovecot: auth(default): passwd(mobile,<ip>): lookup
Jul 20 16:52:34 penguin dovecot: auth(default): master out: USER#0118#011mobile#011system_groups_user=mobile#011uid=1002#011gid=1002#011home=/home/mobile
Jul 20 16:52:34 penguin dovecot: imap-login: Login: user=<mobile>, method=PLAIN, rip=<ip>, lip=192.168.218.119, TLS
Jul 20 16:52:34 penguin dovecot: IMAP(mobile): Effective uid=1002, gid=1002, home=/home/mobile
Jul 20 16:52:34 penguin dovecot: IMAP(mobile): mbox: data=~/mail:INBOX=/var/mail/mobile
Jul 20 16:52:34 penguin dovecot: IMAP(mobile): fs: root=/home/mobile/mail, index=, control=, inbox=/var/mail/mobile
Jul 20 16:52:36 penguin dovecot: IMAP(mobile): Connection closed bytes=128/986

That's all that gets logged.

---

