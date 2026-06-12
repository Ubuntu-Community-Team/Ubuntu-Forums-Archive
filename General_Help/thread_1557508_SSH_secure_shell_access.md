---
title: "SSH secure shell access"
date: 2010-08-20
forum: General Help
---

### Post by Vtsedi on 2010-08-20
How to SSH secure shell access to block root logins and display a warning banner at login

---

### Post by holiday on 2010-08-20
> **Vtsedi said:**
> How to SSH secure shell access to block root logins and display a warning banner at login

Open up /etc/ssh/sshd.config and set the PermitRootLogin property to no.

I don't know about the warning banner. As far as I'm concerned if someone's trying to login as root, they get nothing.

---

### Post by Morrad on 2010-08-21
> **Vtsedi said:**
> How to SSH secure shell ... display a warning banner at login

For the banner, you'll want to include in your sshd_config file

```
Banner /path/to/banner
```

My google-fu turned up a quick tutorial: [http://www.cyberciti.biz/tips/change-openssh-sshd-server-login-banner.html](http://www.cyberciti.biz/tips/change-openssh-sshd-server-login-banner.html)

---

