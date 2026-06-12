---
title: "Error with aptitude and tasksel, server"
date: 2011-02-28
forum: General Help
---

### Post by acastrolorenzo on 2011-02-28
Hi everyone.

I am trying to install LAMP server stack on 10.10 ubuntu server.

I tried it first with: sudo tasksel install lamp-server

But recieved the known bug "aptitude 100 error", can read more here: [https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/131134](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/131134)

Then, I tryed to install the whole LAMP by traditional way, starts with:
[B]sudo aptitude install apache2-mpm-prefork

But recieve other error:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main linux-headers-2.6.35-25 all 2.6.35-25.44
  Fallo temporal al resolver 'security.ubuntu.com'
Err [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-headers-2.6.35-25 all 2.6.35-25.44
  Fallo temporal al resolver 'es.archive.ubuntu.com'
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main linux-headers-2.6.35-25 all 2.6.35-25.44
  Fallo temporal al resolver 'security.ubuntu.com'

Translate from sp: temporal error solving "security..."

Whats that?

Thanks in advance!
[/B]

---

### Post by acastrolorenzo on 2011-02-28
By the way, the same problems appears when sudo apt-get update or upgrade :confused:

---

### Post by earlf on 2011-03-30
acastrolorenzo,

I ran into similar problems, and I found a fix. I described my results on [this thread.]("http://ubuntuforums.org/showthread.php?p=10618529#post10618529")
you may have tried this, but I just thought this might help.
good luck!

---

