---
title: "Problem connecting to my postfix mailserver"
date: 2012-07-15
forum: General Help
---

### Post by d3ngar on 2012-07-15
Hi there,

I would need some help understanding where I went wrong when I tried to configure my mail server...

I have followed the guide here: [https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto](https://help.ubuntu.com/community/PostfixCompleteVirtualMailSystemHowto)

And also added some information to the MySQL tables, so I would have a user to log into...

So far so good, but when I try to configure Thunderbird to connect, I get the following in my /var/log/mail.log:

> domU-12-31-39-09-50-45 imapd: Connection, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 pop3d: Connection, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 imapd: Connection, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 pop3d: Connection, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 imapd: LOGOUT, ip=[::ffff:86.140.88.215], rcvd=24, sent=464
domU-12-31-39-09-50-45 imapd: LOGOUT, ip=[::ffff:86.140.88.215], rcvd=24, sent=464
domU-12-31-39-09-50-45 pop3d: LOGOUT, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 pop3d: Disconnected, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 pop3d: LOGOUT, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 pop3d: Disconnected, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 postfix/smtpd[12018]: connect from host86-140-88-215.range86-140.btcentralplus.com[86.140.88.215]
domU-12-31-39-09-50-45 postfix/smtpd[12023]: connect from host86-140-88-215.range86-140.btcentralplus.com[86.140.88.215]
domU-12-31-39-09-50-45 postfix/smtpd[12018]: improper command pipelining after EHLO from host86-140-88-215.range86-140.btcentralplus.com[86.140.88.215]
domU-12-31-39-09-50-45 postfix/smtpd[12018]: disconnect from host86-140-88-215.range86-140.btcentralplus.com[86.140.88.215]
domU-12-31-39-09-50-45 postfix/smtpd[12023]: disconnect from host86-140-88-215.range86-140.btcentralplus.com[86.140.88.215]
domU-12-31-39-09-50-45 imapd: Connection, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 imapd: LOGIN FAILED, method=PLAIN, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 imapd: LOGIN FAILED, user=chris, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 imapd: Disconnected, ip=[::ffff:86.140.88.215], time=11, starttls=1
domU-12-31-39-09-50-45 imapd: Connection, ip=[::ffff:86.140.88.215]
JdomU-12-31-39-09-50-45 imapd: LOGIN FAILED, method=PLAIN, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 imapd: LOGIN FAILED, user=chris@mydomain.com, ip=[::ffff:86.140.88.215]
domU-12-31-39-09-50-45 imapd: Disconnected, ip=[::ffff:86.140.88.215], time=12, starttls=1


I understand that the mailserver is actually listening and that the DNS is working correctly. 
What I don't know is what user information I would need to use. I would appreciate the help of someone that knows this stuff a little.

Thanks,

Chris

---

### Post by d3ngar on 2012-07-15
It seems that the problem might not be postfix, but courier...

---

### Post by d3ngar on 2012-11-18
I did manage to set-up my mail server in the end.

---

### Post by dcstar on 2012-11-19
> **d3ngar said:**
> I did manage to set-up my mail server in the end.

Then MARK the thread!

---

