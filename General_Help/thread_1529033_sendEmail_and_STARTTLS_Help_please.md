---
title: "sendEmail and STARTTLS Help please"
date: 2010-07-11
forum: General Help
---

### Post by william_lane on 2010-07-11
':~$ sendEmail -f [email]w@hotmail.com[/email] -t [email]w1@gmail.com[/email] -cc [email]w@gmail.com[/email] -u "Message title" -m "The body of the message" -s smtp.live.com:587 -xu [email]w@hotmaill.com[/email] -xp mypassword'

Jul 11 13:59:26 wl-base-d sendEmail[2140]: NOTICE => Authentication not supported by the remote SMTP server!
Jul 11 13:59:26 wl-base-d sendEmail[2140]: ERROR => Received:     530 5.7.0 Must issue a STARTTLS command first
Does anyone know how to use the STARTTLS command to make my sendEmail work?
Thank You to who every replies:D

---

### Post by dcstar on 2010-07-12
> **william_lane said:**
> ':~$ sendEmail -f [email]w@hotmail.com[/email] -t [email]w1@gmail.com[/email] -cc [email]w@gmail.com[/email] -u "Message title" -m "The body of the message" -s smtp.live.com:587 -xu [email]w@hotmaill.com[/email] -xp mypassword'

Jul 11 13:59:26 wl-base-d sendEmail[2140]: **NOTICE => Authentication not supported by the remote SMTP server!**
Jul 11 13:59:26 wl-base-d sendEmail[2140]: ERROR => Received:     530 5.7.0 Must issue a STARTTLS command first
Does anyone know how to use the START**TLS** command to make my sendEmail work?
Thank You to who every replies:D

If you read the man page, it does not mention that it can connect using TLS.

---

