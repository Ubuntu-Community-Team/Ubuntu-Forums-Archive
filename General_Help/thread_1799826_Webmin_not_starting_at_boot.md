---
title: "Webmin not starting at boot"
date: 2011-07-08
forum: General Help
---

### Post by BrandonSk on 2011-07-08
Hello all,

I just reinstalled Ubuntu server. So I have a pretty clean installation with LAMP and OpenSSH.

Then I installed webmin (I had it running previously, so I used the same steps).
The problem is that webmin server does not start at boot.
It can be started manually by sudo /etc/webmin/start
or just simply by /etc/webmin start    if I am logged in as root.

However, if I try starting it as any other user without sudo, I receive the following error:
> Failed to open config file /etc/webmin/miniserv.conf : Permission denied at /srv/Repository/webmin/webmin-1.550/miniserv.pl line 4230.I suspect that this permission issue has something to do with Webmin not starting at boot.

Permisions on the miniserv.pl file are 755 with "root" as owner and group "bin".

Any ideas how I can get the webmin started at boot?

Thank you very much in advance.
Cheers,
B.

---

