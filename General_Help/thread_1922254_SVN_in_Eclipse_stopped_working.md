---
title: "SVN in Eclipse stopped working"
date: 2012-02-08
forum: General Help
---

### Post by taotree on 2012-02-08
Yesterday, my SVN (Subversive) inside in eclipse stopped working. I rebooted yesterday and so it applied some updates that required rebooting. I'm wondering if possibly there was something int he new updates that might affect it?

I can access the subversion URL (it's using http protocol) in a browser just fine. But for SVN operations from eclipse it gives me:

Synchronize operation failed.
svn: can not read HTTP status line
svn: OPTIONS request failed on '/repos/projects/service/AnalystServices/trunk'

Hmm... not just eclipse. When I click the "Check" button in Update Manager, I get:

W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg](http://archive.canonical.com/ubuntu/dists/oneiric/Release.gpg)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-amd64/Packages)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/binary-i386/Packages)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en](http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Translation-en)  Connection failed [IP: 127.0.0.1 8080]
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-amd64/Packages)  Connection failed [IP: 127.0.0.1 8080]

---

### Post by taotree on 2012-02-08
Figured it out. Apparently I had a proxy configured in eclipse in the general->network connections preferences.

---

