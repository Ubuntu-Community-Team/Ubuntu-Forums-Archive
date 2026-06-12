---
title: "Sending error in Evolution"
date: 2006-03-30
forum: General Help
---

### Post by etherealbeats on 2006-03-30
I have set up Evolution with my POP3 account. I can receive mail but when I try to send I get the following message: "Host lookup failed:  auth.smtp.1and1.co.uk: Name or service not known".

The SMTP server does require authentication but there are so many different types for the SMTP, and the ones I've tried aren't working.

Any ideas?

Thanks,
J.

---

### Post by ranf on 2006-03-30
Can you ping this host?
```
ping auth.smtp.1and1.co.uk
```

Can you telnet to the smtp port?
```

ranf@schlepp:~ $ telnet auth.smtp.1and1.co.uk 25
Trying 212.227.15.179...
Connected to auth.smtp.1and1.co.uk.
Escape character is '^]'.
220 auth.smtp.oneandone.co.uk (mrelayeu5) Welcome to Nemesis ESMTP server
helo ranf
250 mrelayeu5.kundenserver.de pleased to meet you
bye
500 unknown command
quit
221 auth.smtp.oneandone.co.uk Bye
Connection closed by foreign host.

```

---

### Post by etherealbeats on 2006-03-30
Yes, pinged and telneted it fine, I've been using the same SMTP server for my email on Outlook in Windows and had no problems before.

---

### Post by etherealbeats on 2006-03-30
Fixed it, was messing around and realised there was a space before the name of the server in the settings. Silly me.

Thanks for your help.

---

