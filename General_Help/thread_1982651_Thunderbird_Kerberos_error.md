---
title: "Thunderbird Kerberos error"
date: 2012-05-18
forum: General Help
---

### Post by r.stiltskin on 2012-05-18
I'm trying to set up an email account that uses no encryption so I configured it in Thunderbird account settings as 
Connection security: None
Authentication method: Password, transmitted insecurely
but when I try to send an email I get this error dialog:

Sending of message failed
The Kerberos/GSSAPI ticket was not accepted by the SMTP server ...
Please check that you are logged in to the Kerberos/GSSAPI realm.

Why?

Thunderbird 12.0.1 Kubuntu 11.10

---

### Post by steeldriver on 2012-05-18
are you sure you are looking at "Outgoing Server (SMTP)"  not "Server Settings"?

---

### Post by r.stiltskin on 2012-05-19
Duh...

I hate to say how much time I spent staring at this damn thing and not seeing that.  I never noticed that at the bottom of the list until you gave me the exact wording.

Thanks.

---

