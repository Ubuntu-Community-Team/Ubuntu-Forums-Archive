---
title: "Using mail/sendmail to send email to local email server"
date: 2009-12-10
forum: General Help
---

### Post by stefanadelbert on 2009-12-10
I'm trying to send an email from a bash script on TheBox using mail (sendmail) to an email address (e.g. [email]admin@example.com[/email]) on a local mail server, TheMailServer, running postfix and dovecot. For some reason the email doesn't hit TheMailServer at all (I'm tailing /var/log/mail.info and see nothing). TheBox is timing out when attempting to contact the mail server according to the logs. However, TheBox able to send email to gmail.com without problems.

I have a feeling that this is because the MX record, example.com, is being resolved by our external DNS service to the static IP of our modem (according to nslookup anyway). It should route port 25 through to our mail server and this works fine from outside our network. But maybe that routing is not working for TheBox because it's on the local network. Is there a way to resolve the MX record on TheBox by using /etc/hosts or something similar?

---

