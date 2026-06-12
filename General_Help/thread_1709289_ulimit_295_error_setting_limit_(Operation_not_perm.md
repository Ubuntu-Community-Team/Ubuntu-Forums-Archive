---
title: "ulimit: 295: error setting limit (Operation not permitted)"
date: 2011-03-18
forum: General Help
---

### Post by nkae100 on 2011-03-18
I am running the SMTP server Xeams as a non-root users.

When I run the program I get the following error:

ulimit: 295: error setting limit (Operation not permitted)

When I am root it works fine. As its an SMTP server, I am so not running it as root. Can anyone suggest how to get it working for non-root users? Someone suggested "PAM config files" and that "per-user limit settings cannot override PAM limits" on another forum in /etc/security/limits.conf and etc/security/limits.d/... but I have no idea what thats in reference to. :(

---

