---
title: "Clamav update problem.."
date: 2010-03-01
forum: General Help
---

### Post by karthick87 on 2010-03-01
I am using clamav antivirus but when i try to update the virus definitions it shows some errors...What it mean?

> karthick@Learners-desktop:~$ sudo freshclam
ClamAV update process started at Mon Mar  1 11:45:28 2010
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.95.1 Recommended version: 0.95.3
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
Downloading main-52.cdiff [100%]
main.cld updated (version: 52, sigs: 704727, f-level: 44, builder: sven)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 42, recommended = 44
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
WARNING: getfile: daily-10370.cdiff not found on remote server (IP: 219.106.242.51)
WARNING: getpatch: Can't download daily-10370.cdiff from db.local.clamav.net
Trying host db.local.clamav.net (211.239.150.206)...
WARNING: getfile: daily-10370.cdiff not found on remote server (IP: 211.239.150.206)
WARNING: getpatch: Can't download daily-10370.cdiff from db.local.clamav.net
Trying host db.local.clamav.net (211.239.150.206)...
WARNING: getfile: daily-10370.cdiff not found on remote server (IP: 211.239.150.206)
WARNING: getpatch: Can't download daily-10370.cdiff from db.local.clamav.net
Trying host db.local.clamav.net (211.239.150.206)...
WARNING: getfile: daily-10370.cdiff not found on remote server (IP: 211.239.150.206)
WARNING: getpatch: Can't download daily-10370.cdiff from db.local.clamav.net
WARNING: getfile: daily-10370.cdiff not found on remote server (IP: 218.44.253.75)
WARNING: getpatch: Can't download daily-10370.cdiff from db.local.clamav.net
WARNING: Incremental update failed, trying to download daily.cvd
Downloading daily.cvd [100%]
daily.cvd updated (version: 10471, sigs: 19704, f-level: 44, builder: guitar)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 42, recommended = 44
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
Database updated (724431 signatures) from db.local.clamav.net (IP: 120.29.176.126)
Clamd successfully notified about the update.

---

### Post by MooPi on 2010-03-01
Not certain but seems the only version included with Jaunty is out dated. Try this ppa
[https://launchpad.net/~ubuntu-clamav/+archive/ppa]("https://launchpad.net/%7Eubuntu-clamav/+archive/ppa")
Add the source lists to your /etc/apt/sources.list and then update and upgrade
```
sudo apt-get update
``````
sudo apt-get upgrade
```Clamav should update to the most current

---

### Post by dcstar on 2010-03-01
> **MooPi said:**
> Not certain but seems the only version included with Jaunty is out dated.
........

Why do you think that the messages say "**DON'T PANIC!**"?

Is is **not** that important that the version is slightly out of date, the Ubuntu package maintainers will update anything important, Clamav has many trivial updates and will never be updated to the latest version because it usually isn't worth the trouble.

---

