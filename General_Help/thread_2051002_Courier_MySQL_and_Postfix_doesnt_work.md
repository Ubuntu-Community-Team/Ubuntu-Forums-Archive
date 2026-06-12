---
title: "Courier MySQL and Postfix doesnt work"
date: 2012-09-01
forum: General Help
---

### Post by The Sorrow on 2012-09-01
So i followed [_[COLOR="Blue"]THIS[/COLOR]_]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.10") tutorial only slightly tweaking the setup for a separately hosted MySQL server. when i try to connect to the server via thunderbird i get the following log messages




```

Aug 31 22:19:31 InternalMAILSRV pop3d: Connection, ip=[::ffff:10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV pop3d: Connection, ip=[::ffff:10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV pop3d: LOGOUT, ip=[::ffff:10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV pop3d: Disconnected, ip=[::ffff:10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV pop3d: LOGOUT, ip=[::ffff:10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV pop3d: Disconnected, ip=[::ffff:10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV postfix/smtpd[3794]: connect from unknown[10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV postfix/smtpd[3794]: disconnect from unknown[10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV postfix/smtpd[3794]: connect from unknown[10.x.x.x]
Aug 31 22:19:31 InternalMAILSRV postfix/smtpd[3794]: disconnect from unknown[10.x.x.x]
Aug 31 22:19:37 InternalMAILSRV postfix/smtpd[3794]: connect from unknown[10.x.x.x]
Aug 31 22:19:37 InternalMAILSRV postfix/smtpd[3794]: improper command pipelining after EHLO from unknown[10.x.x.x]: QUIT\r\n
Aug 31 22:19:37 InternalMAILSRV postfix/smtpd[3794]: disconnect from unknown[10.x.x.x]
Aug 31 22:19:37 InternalMAILSRV postfix/smtpd[3796]: connect from unknown[10.x.x.x]
Aug 31 22:19:37 InternalMAILSRV imapd: Connection, ip=[::ffff:10.x.x.x]
Aug 31 22:19:37 InternalMAILSRV postfix/smtpd[3796]: lost connection after CONNECT from unknown[10.x.x.x]
Aug 31 22:19:37 InternalMAILSRV postfix/smtpd[3796]: disconnect from unknown[10.x.x.x]
Aug 31 22:19:37 InternalMAILSRV imapd: LOGOUT, ip=[::ffff:10.x.x.x], rcvd=24, sent=464
Aug 31 22:19:38 InternalMAILSRV imapd: Connection, ip=[::ffff:10.x.x.x]
Aug 31 22:19:38 InternalMAILSRV imapd: LOGIN FAILED, method=PLAIN, ip=[::ffff:10.x.x.x]
Aug 31 22:19:43 InternalMAILSRV imapd: LOGIN FAILED, user=user@domain.org, ip=[::ffff:10.x.x.x]

```

I also installed a postfixadmin instance to manage the users and virtual domains instead of the suggested one. SMTP and all the sql integration works fine. I create users and domains, they populate in the SQL database no problem. I try to get connected via thunderbird i get the above. However if i use squirrelmail i get this:


```
Aug 31 22:29:11 InternalMAILSRV imapd: Connection, ip=[::ffff:127.0.0.1]
Aug 31 22:29:11 InternalMAILSRV imapd: LOGIN FAILED, user=user@domain.org, ip=[::ffff:127.0.0.1]
Aug 31 22:29:16 InternalMAILSRV imapd: LOGOUT, ip=[::ffff:127.0.0.1], rcvd=60, sent=332

```

I understand that this isnt much information, but i would like to narrow down what the issue is. My guess is its courier's POP3 and IMAP not working correctly with the SQL integration. Not sure. OS is Ubuntu 12.04.1 LTS.

---

