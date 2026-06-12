---
title: "Filezilla fails to resolve domain"
date: 2010-07-24
forum: General Help
---

### Post by TurboTippy on 2010-07-24
Hi there, I'm having a strange issue with Filezilla that doesn't affect any other apps.

I know my network isnt IPv6 friendly, so I've disabled it in Firefox and in Ubuntu - everything bar Filezilla finds and resolves addresses properly. Filezilla just gives me the responses below, trying to connect to 1.0.0.0:21 for any domain I try to FTP to.

If I then go to terminal and do an ftp ftp.asdad.com etc, once terminal has resolved the domain, filezilla works - very odd. Any ideas how I can stop having to do this step in terminal?

Status:    Resolving address of ftp.xxxx
Status:    Connecting to 1.0.0.0:21...
Error:    Connection timed out
Error:    Could not connect to server
Status:    Waiting to retry...
Status:    Delaying connection for 1 second due to previously failed connection attempt...
Status:    Delaying connection for 1 second due to previously failed connection attempt...
Status:    Resolving address of ftp.xxxxx
Status:    Connecting to 1.0.0.0:21...

---

### Post by TurboTippy on 2010-08-16
Any ideas? This is still occurring.

---

### Post by pgacv2 on 2010-10-16
I was able to fix it with Edit -> Settings -> FTP -> Transfer Mode: Passive. Hope it helps.

---

