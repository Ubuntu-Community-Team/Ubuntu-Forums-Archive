---
title: "Postfix download all my email to postmaster email address and not to the local users."
date: 2009-07-01
forum: General Help
---

### Post by kameelperdza on 2009-07-01
Hi im having trouble setting up [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)
 
I have followed all the steps but it stil unable to recieve mail correctly. 
 
In the mail.log is shows that all messages in been send to the postmaster address that i have spesified in the fetchmailrc file.
 
[SIZE=1]Jun 30 17:02:58 Apie fetchmail[4676]: Server CommonName mismatch: jcwhosting02.theplanet.host != mail.kleinkarootoyota.co.za [/SIZE]
[SIZE=1]Jun 30 17:02:58 Apie fetchmail[4676]: Server certificate verification error: self signed certificate [/SIZE]
[SIZE=1]Jun 30 17:03:01 Apie fetchmail[4676]: sleeping at Tue 30 Jun 2009 17:03:01 SAST for 30 seconds [/SIZE]
[SIZE=1]Jun 30 17:03:31 Apie fetchmail[4676]: awakened at Tue 30 Jun 2009 17:03:31 SAST [/SIZE]
[SIZE=1]Jun 30 17:03:32 Apie fetchmail[4676]: Server CommonName mismatch: jcwhosting02.theplanet.host != mail.kleinkarootoyota.co.za [/SIZE]
[SIZE=1]Jun 30 17:03:32 Apie fetchmail[4676]: Server certificate verification error: self signed certificate [/SIZE]
[SIZE=1]Jun 30 17:03:34 Apie fetchmail[4676]: 1 message for [EMAIL="catchall@kleinkarootoyota.co.za"]catchall@kleinkarootoyota.co.za[/EMAIL] at mail.kleinkarootoyota.co.za (18583 octets). [/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie fetchmail[4676]: reading message [email]catchall@kleinkarootoyota.co.za@kleinkarootoyota.co.za[/email]:1 of 1 (18583 octets) (log message incomplete)[/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie fetchmail[4676]: connection to localhost:smtp [::1/25] failed: Connection refused. [/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/smtpd[4790]: connect from localhost[127.0.0.1][/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/smtpd[4790]: NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 550 5.1.1 <catchall@localhost>: Recipient address rejected: User unknown in local recipient table; from=<correspondence@abelusi.co.za> to=<catchall@localhost> proto=ESMTP helo=<Apie.KKT>[/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie fetchmail[4676]: SMTP error: 550 5.1.1 <catchall@localhost>: Recipient address rejected: User unknown in local recipient table [/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie fetchmail[4676]: connection to localhost:smtp [::1/25] failed: Connection refused. [/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/smtpd[4793]: connect from localhost[127.0.0.1][/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/smtpd[4793]: 89B4071A2E7: client=localhost[127.0.0.1][/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie fetchmail[4676]: mail from [EMAIL="MAILER-DAEMON@Apie.KKT"]MAILER-DAEMON@Apie.KKT[/EMAIL] bounced to [EMAIL="catchall@kleinkarootoyota.co.za"]catchall@kleinkarootoyota.co.za[/EMAIL] [/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/cleanup[4794]: 89B4071A2E7: message-id=<20090630150335.89B4071A2E7@localhost>[/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/qmgr[4640]: 89B4071A2E7: from=<>, size=3407, nrcpt=1 (queue active)[/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/smtpd[4790]: 95EED71A318: client=localhost[127.0.0.1][/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/smtpd[4793]: disconnect from localhost[127.0.0.1][/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/virtual[4795]: 89B4071A2E7: to=<catchall@kleinkarootoyota.co.za>, relay=virtual, delay=0.06, delays=0.05/0.01/0/0, dsn=2.0.0, status=sent (delivered to maildir)[/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/qmgr[4640]: 89B4071A2E7: removed[/SIZE]
[SIZE=1]Jun 30 17:03:35 Apie postfix/cleanup[4794]: 95EED71A318: message-id=<20090630145859.F15A9F8F2C@mx1.abelusi.co.za>[/SIZE]
[SIZE=1]Jun 30 17:03:36 Apie fetchmail[4676]: flushed [/SIZE]
[SIZE=1]Jun 30 17:03:36 Apie postfix/qmgr[4640]: 95EED71A318: from=<correspondence@abelusi.co.za>, size=18911, nrcpt=1 (queue active)[/SIZE]
[SIZE=1]Jun 30 17:03:36 Apie postfix/virtual[4795]: 95EED71A318: to=<catchall@kleinkarootoyota.co.za>, relay=virtual, delay=0.83, delays=0.82/0/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)[/SIZE]
[SIZE=1]Jun 30 17:03:36 Apie postfix/qmgr[4640]: 95EED71A318: removed[/SIZE]
[SIZE=1]Jun 30 17:03:37 Apie fetchmail[4676]: sleeping at Tue 30 Jun 2009 17:03:37 SAST for 30 seconds[/SIZE]
 
[SIZE=1]Here is my plan....i connect to the isp mail server and download all the emails using catchall account. Then i create new users on my mail server and my poeple can download their mail internally. That would help becos then i can control everything.[/SIZE]
 
[SIZE=1]My fetchmailrc looks like this[/SIZE]
 
[SIZE=1][SIZE=1]set no bouncemail[/SIZE]
[SIZE=1]set syslog;[/SIZE]
[SIZE=1]set daemon 30;[/SIZE]
[SIZE=1]set postmaster "catchall@kleinkarootoyota.co.za";[/SIZE]
[SIZE=1]poll "mail.kleinkarootoyota.co.za"[/SIZE]
[SIZE=1]with protocol pop3[/SIZE]
[SIZE=1]user "catchall@kleinkarootoyota.co.za" password "xxxxxxxx" is xxxxxxx here [/SIZE]
[SIZE=1]fetchall[/SIZE]
[SIZE=1]ssl[/SIZE]
[SIZE=1]smtphost "localhost" hostname "kleinkarootoyota.co.za"[/SIZE]
 
 
 
[SIZE=1]Anyone that can tell me what im doing wrong would help alot, Im trying to solve this issue for 2 months now and dont know what to do anyone.[/SIZE]
 
[SIZE=1]thankyou[/SIZE]
[/SIZE]

---

### Post by kameelperdza on 2009-07-02
Im giving up, i cant take it anymore, no one ant to help me. Im getting no were.  :-(

---

