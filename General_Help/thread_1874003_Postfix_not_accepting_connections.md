---
title: "Postfix not accepting connections"
date: 2011-11-02
forum: General Help
---

### Post by haarvik on 2011-11-02
Ok, so I have been banging my head for two days on this, and cannot figure it out.  I have Postfix setup on Ubuntu 10.04.  I have a firewall that forwards traffic to my box, all traffic.  I can telnet to port 25 from localhost and the local network.  I cannot, however connect from outside.  I have checked everything I have read for allowing incoming connections.  I know it's not an ISP blocking thing because I have a Windows server that accepts email just fine.  

Reaching for straws here, but am I missing something??

---

### Post by haarvik on 2011-11-02
Ok, update.  yes my firewall was blocking port 25.  however I have a new issue.  I am using Thunderbird as a client to connect.  My log file spits this out:

Nov  2 10:57:52 inventory postfix/smtpd[11798]: improper command pipelining after EHLO from host-66-202-61-82.ind.choiceone.net[66.202.61.82]
Nov  2 10:57:52 inventory postfix/smtpd[11798]: disconnect from host-66-202-61-82.ind.choiceone.net[66.202.61.82]

and I cannot set the client up.  I have searched for this error, and have found nothing.  HELP!!!

---

### Post by tonysathre on 2011-11-02
Did you forward the port to your Linux box? Try shutting down the SMTP service on your Windows box.

Also, whats the output of:

```
dig mx yourdomain.com
```

Is the 'Windows Server' an actual SMTP server or just a client that pulls email from your Linux SMTP server? If so it's probably a port conflict with your Windows box. Try changing the listening port on your Linux box.

---

