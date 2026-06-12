---
title: "Can't send Bigpond email"
date: 2011-02-21
forum: General Help
---

### Post by Brian_G_M on 2011-02-21
Hi,
I have recently installed Ubuntu 10.04 on an Asus EEE netbook, and using Evolution for email. I set up to send and receive Gmail OK (using POP3) and Bigpond mail receives OK but sending doesn't work - I get a message that it timed out trying to connect to SMTP server. I have been over and over this, checking the settings from the bigpond site. I installed Thunderbird and tried that, same result. I tried setting up the account again, I tried varying all the settings I can find, I have tried it with a Telstra dongle and with a wifi connection, always the same result. 
What might I be missing?
Thanks for any helpful suggestions anyone can offer.

---

### Post by Habitual on 2011-02-21
2 emails accounts? Or are you just sending from gMail to BigPond?
If 2 accounts, then is bigpond setup for IMAP or POP?

---

### Post by Brian_G_M on 2011-02-21
Two accounts. Bigpond is setup for POP.

---

### Post by Habitual on 2011-02-21
telnet to it on port 25 like so...

```
telnet mail.bigpond.com 25
```
You should see this.

Trying 61.9.189.249...
Connected to mail.bigpond.com.
Escape character is '^]'.
220 nschwotgx02p.mx.bigpond.com ESMTP server ready Tue, 22 Feb 2011 01:18:12 +0000

Please let is know...

---

### Post by Brian_G_M on 2011-02-22
Thanks.
I did, I get this response (twice)
Trying 61.9.189.249...
Trying 61.9.168.249...
telnet: Unable to connect to remote host: Connection timed out
Looks like the problem is not in my email settings. What should I do?
Thanks for your help.
Brian

---

### Post by Clever_Username on 2011-02-22
Try this and post results

```
telnet localhost 25
```

---

### Post by TopEnder on 2011-02-22
Brian, Do yo have anything set in your account's Security Encryption (eg: TSL or SSL)?  If so change your setting to No Encryption and see if you can connect to the Bigpond server.  I have never been able to setup a Secure Send connection.  TopEnder

---

### Post by Brian_G_M on 2011-02-22
Clever_Username: telnet localhost 25 gave this result:

Trying ::1...
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

Top-ender, no I set to no encription

---

### Post by Cfossy2 on 2012-12-27
I also had the same problem, but rectified it by first changing server SMTP to mail.bigpond.com and port to 25. This seemed to have made all the difference.I was then able to send emails through thunderbird from my bigpond account.

Cfossy2

:D

---

