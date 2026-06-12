---
title: "smtp running at start up then stops..."
date: 2011-04-24
forum: General Help
---

### Post by Mia_tech on 2011-04-24
guys, I was looking for a way to send email to the outside world and installed mutt, and noticed that when my pc starts port :25 smtp is up, so I figured that I could send email to the outside, after a few seconds it shuts down.... what could that be? and do I need to install a full flesh mail server in order to send outbound email?

thanks

---

### Post by HermanAB on 2011-04-24
Did you install a SMTP agent such as Postfix or Citadel?

---

### Post by terrapin893 on 2011-04-24
As for why the application stops running, don't know, maybe check the logs?  

Regarding sending mail you will need a MTA (mail transfer agent) . . . such as Postfix, Sendmail or Exim.

---

### Post by Mia_tech on 2011-04-24
> **HermanAB said:**
> Did you install a SMTP agent such as Postfix or Citadel?

the only thing I installed was mutt, does mutt installation also install any smtp agents?

---

### Post by Mia_tech on 2011-04-24
> **terrapin893 said:**
> As for why the application stops running, don't know, maybe check the logs?  

Regarding sending mail you will need a MTA (mail transfer agent) . . . such as Postfix, Sendmail or Exim.

which one is the easiest to learn/configure? how about mailx?

---

### Post by Mia_tech on 2011-04-24
ok, I just checked and I have exim4 installed... and the logs are showing this
2011-04-24 01:26:53 socket bind() to port 25 for address ::1 failed: Cannot assign requested address: waiting 30s before trying again (9 more tries)
and this: Mailing to remote domains not supported

---

### Post by andrew.46 on 2011-04-24
You might consider installing something simply like msmtp to send your mail. This requires the following in your ~/.muttrc file:

```
set sendmail="/usr/bin/msmtp"  
```

and then the appropriate configuration in ~/.msmtprc.

---

