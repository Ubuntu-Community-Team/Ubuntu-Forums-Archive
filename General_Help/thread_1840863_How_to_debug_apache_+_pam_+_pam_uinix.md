---
title: "How to debug apache + pam + pam_uinix"
date: 2011-09-08
forum: General Help
---

### Post by couling on 2011-09-08
Hi All

I'm trying to get a section of my intranet to authenticate with system passwords through pam.  I'm reasonably experienced at working with apache configuration but very new to PAM.

The problem I'm facing is that it's just not letting me login and I'm struggling to find any helpful debug output.

Any hints on what I may have donw wrong or how I can get more helpful debug would be great.

Apache error log for the vhost lists:```
[Thu Sep 08 14:20:52 2011] [error] [client 127.0.0.1] PAM: user 'phil' - not authenticated: Authentication failure

```/var/log/auth lists:```
Sep  8 14:20:50 zbox unix_chkpwd[4739]: check pass; user unknown
Sep  8 14:20:50 zbox unix_chkpwd[4739]: password check failed for user (phil)
Sep  8 14:20:50 zbox apache2: pam_unix(apache2:auth): authentication failure; logname= uid=33 euid=33 tty= ruser= rhost=127.0.0.1  user=phil

```
/etc/pam.d/apache2 is configured as ```
auth      required  pam_securetty.so
auth      required  pam_unix.so shadow audit
auth      required  pam_nologin.so
account   required  pam_unix.so

```Relavent apache config for the vhost :
```
    <Directory / >
        AuthPAM_Enabled on
        AuthType Basic
        AuthName "svn.pedal.me.uk"
    </Directory>

...


    <Directory /path/to/content >
        Options Indexes FollowSymLinks
        AllowOverride None

        Order allow,deny
        Allow from all

        require user phil
    </Directory>


```

---

### Post by couling on 2011-09-13
Ah I've managed to answer my own question.

In the interests of keeping thread counts down, I've posted the answer here.

[http://www.linuxquestions.org/questions/linux-software-2/how-to-debug-apache-pam-pam_uinix-901950/](http://www.linuxquestions.org/questions/linux-software-2/how-to-debug-apache-pam-pam_uinix-901950/)

---

