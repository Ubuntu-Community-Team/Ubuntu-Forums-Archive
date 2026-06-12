---
title: "A simple webpage to start"
date: 2011-04-09
forum: General Help
---

### Post by satimis on 2011-04-09
Hi folks,

OS - Ubuntu 1010 server edition.

I have lighttpd installed.  On browser [http://ipaddress](http://ipaddress) starts the "Placeholder Page"

$ apt-cache policy lighttpd```

lighttpd:
  Installed: 1.4.26-3ubuntu2
  Candidate: 1.4.26-3ubuntu2
  Version table:
 *** 1.4.26-3ubuntu2 0
        500 http://hk.archive.ubuntu.com/ubuntu/ maverick/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Now I'm prepared to create a simple webpage testing it.  Google find me many suggestion.  I hesitate where shall be my starting point.  Please shed me some light.  TIA

B.R.
satimis

---

### Post by spikoley on 2011-04-11
You just need to place the HTML file in the online directory for it to work.  The documentation should show you which directory to place it in.

---

### Post by satimis on 2011-04-11
> **spikoley said:**
> You just need to place the HTML file in the online directory for it to work.  The documentation should show you which directory to place it in.

Hi,

I got it done already.  Thanks.

The HTML file is on /var/www/index.htlm similar to Apache.

Now I'm proceeding on Virtual Hosting.  I do hope it would be similar to Apache as well.

B.R.
satimis

---

### Post by satimis on 2011-04-11
Hi folks,

A further question.

I followed;

Lighttpd virtualhost configuration ~ name-based virtual hosting

[http://www.cyberciti.biz/faq/howto-lighttpd-virtualhost-configuration/](http://www.cyberciti.biz/faq/howto-lighttpd-virtualhost-configuration/)

Where shall I keep the "index.html" file?  TIA

B.R.
satimis

---

