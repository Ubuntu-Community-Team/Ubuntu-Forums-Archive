---
title: "SASL Auth TLS  Postfix Courier  issue"
date: 2011-01-06
forum: General Help
---

### Post by prcwest on 2011-01-06
[INDENT]Hello and sorry about my english...
[/INDENT]I'm new to ubuntu forum and I will start immediately with a problem ;)
I have installed an e mail server on ubuntu 9.10 with Postfix, Courier IMAP, MySQL, Amavisd, SpamAssassin, ClamAV , SASL, TLS . (flurdy.com) external As far as I know everything is working just fine, but internal not.I would like to connect another PC on the internal network to the server with Outlook 2010. I also want to install squirrelmail
bud sasl,tls and imap ssl are not working internal. 
 
I have rechecked all the configurations over and over againand they all seem to be fine. and it works also just fine bud only from external network. I am wondering if you could help me to find the problem....
 
**external connection**
 
```
..authdaemond: authmysql: trying this module
..authdaemond: authmysqllib: connected. Versions: header 50075, client 50083, server 50137
..authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'info@myserver.com'  AND (enabled=1)
..authdaemond: password matches successfully
..authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, [EMAIL="address=info@server.com"]address=info@server.com[/EMAIL], fullname=myserver Info, maildir=/var/spool/mail/virtual/info/, quota=<null>, options=<null>
..authdaemond: authmysql: clearpasswd=<null>, passwd=Mek1lkYheHAi8
..authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, [EMAIL="address=info@myserver.com"]address=info@myserver.com[/EMAIL], fullname=myserver Info, maildir=/var/spool/mail/virtual/info/, quota=<null>, options=<null>
..authdaemond: Authenticated: clearpasswd=12345678, passwd=Mek1lkYheHAi8
..imapd-ssl: LOGIN, [EMAIL="user=info@myserver.com"]user=info@myserver.com[/EMAIL], ip=[::ffff:94.197.110.210], port=[57439], protocol=IMAP
..imapd-ssl: DISCONNECTED, [EMAIL="user=info@myserver.com"]user=info@myserver.com[/EMAIL], ip=[::ffff:94.197.110.210], headers=9692, body=71291, rcvd=2950, sent=101560, time=41, starttls=1

```
 
**internal ssl,tls and sasl**
```
 
..imapd: Connection, ip=[::ffff:192.168.0.4]
..imapd: Disconnected, ip=[::ffff:192.168.0.4], time=0
..imapd: Connection, ip=[::ffff:192.168.0.4]
..imapd-ssl: Connection, ip=[::ffff:192.168.0.4]
..imapd-ssl: Unexpected SSL connection shutdown.
..imapd-ssl: Disconnected, ip=[::ffff:192.168.0.4], time=0, starttls=1
..imapd: Unexpected SSL connection shutdown.
..imapd: Disconnected, ip=[::ffff:192.168.0.4], time=0, starttls=1
..imapd: Connection, ip=[::ffff:192.168.0.4]
..imapd: Disconnected, ip=[::ffff:192.168.0.4], time=0
..imapd: Connection, ip=[::ffff:192.168.0.4]
..imapd: Disconnected, ip=[::ffff:192.168.0.4], time=0
..imapd: Connection, ip=[::ffff:192.168.0.4]
..imapd: Connection, ip=[::ffff:192.168.0.4]
..imapd: Disconnected, ip=[::ffff:192.168.0.4], time=0
..imapd: Unexpected SSL connection shutdown.
..imapd-ssl: Unexpected SSL connection shutdown.
..imapd-ssl: Connection, ip=[::ffff:192.168.0.4]
..imapd: Disconnected, ip=[::ffff:192.168.0.4], time=1, starttls=1
postfix/smtpd[3316]: connect from unknown[192.168.0.4]
postfix/smtpd[3316]: warning: SASL authentication failure: realm changed: authentication aborted
postfix/smtpd[3316]: warning: unknown[192.168.0.4]: SASL DIGEST-MD5 authentication failed: authentication failure
postfix/smtpd[3315]: warning: SASL authentication failure: realm changed: authentication aborted
postfix/smtpd[3315]: warning: unknown[192.168.0.4]: SASL DIGEST-MD5 authentication failed: authentication failure
postfix/smtpd[3316]: lost connection after AUTH from unknown[192.168.0.4]
postfix/smtpd[3316]: disconnect from unknown[192.168.0.4]

```
 
**internal connection Imap(143) working**
```
 
..imapd: Connection, ip=[::ffff:192.168.0.4]
..authdaemond: received auth request, service=imap, authtype=login
..authdaemond: authmysql: trying this module
..authdaemond: SQL query: SELECT id, crypt, "", uid, gid, home, concat(home,'/',maildir), "", name, "" FROM users WHERE id = 'info@myserver.com'  AND (enabled=1)
..authdaemond: password matches successfully
..authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, [EMAIL="address=info@myserver.com"]address=info@myserver.com[/EMAIL], fullname=myserver Info, maildir=/var/spool/mail/virtual/info/, quota=<null>, options=<null>
..authdaemond: authmysql: clearpasswd=<null>, passwd=Mek1lkYheHAi8
..authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/var/spool/mail/virtual, [EMAIL="address=info@myserver.com"]address=info@myserver.com[/EMAIL], fullname=myserver Info, maildir=/var/spool/mail/virtual/info/, quota=<null>, options=<null>
..authdaemond: Authenticated: clearpasswd=12345678, passwd=Mek1lkYheHAi8
..imapd: LOGIN, [EMAIL="user=info@myserver.com"]user=info@myserver.com[/EMAIL], ip=[::ffff:192.168.0.4], port=[62804], protocol=IMAP
..imapd: LOGOUT, [EMAIL="user=info@myserver.com"]user=info@myserver.com[/EMAIL], ip=[::ffff:192.168.0.4], headers=0, body=980, rcvd=294, sent=3298, time=10

```
 
Thanks for any assistance you can provide

---

