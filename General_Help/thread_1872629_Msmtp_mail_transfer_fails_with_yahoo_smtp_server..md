---
title: "Msmtp mail transfer fails with yahoo smtp server."
date: 2011-10-31
forum: General Help
---

### Post by gardnan on 2011-10-31
Hi All.

Today I tried to set up a mutt/msmtp system so that I could send email via the command line. After going through many guides, nearly all of them relating specifically to Gmail, I was wondering if there was anyone out there that had any experience setting up such a system to use Yahoo mail. So far, what I have for my config files for the two programs is:

msmtp:

```
account default
host smtp.yahoo.com
syslog on
tls on
tls_starttls on
tls_trust_file /etc/ssl/certs/ca-certificates.crt
auth on
port 587
from username@yahoo.com
user username
password my-password
```mutt:

```
set from = "username@yahoo.com"
set use_from = yes
set envelope_from = "yes"
set sendmail = "/usr/bin/msmtp"

```With this configuration, msmtp just says:
The server does not support TLS via the STARTTLS command
msmtp could not send mail

I, out of desperation, tried to send an email with tls_starttls set to no, but then the process just hung, after which I decided that trying to connect without TLS would not be something that someone unfamiliar to the TLS protocol  should do.

I also tried the configuration with both ports 587 and 465, but both have the same problem.

My best guess for this problem is that either the certificate I am using does not work for Yahoo, or that Yahoo has a very different setup than Gmail does.

If anyone would be willing to help me I would be very grateful, as I know next to nothing about TLS and TLS Certificates and the like.

---

### Post by gardnan on 2011-11-01
Hi again.

After doing a little research, I realized that STARTTLS was not required for a secure connection and that it could disabled safely for Yahoo mail. After that, I found out that the main cause of my problems was, stupidly, the fact that I left part of Yahoo's smtp server URL (it is actually smtp.mail.yahoo.com).

Anyway, I consider this thread closed, and if you had seen my thread and tried to figure out my problem, thanks anyway.

---

