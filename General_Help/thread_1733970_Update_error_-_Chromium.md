---
title: "Update error - Chromium"
date: 2011-04-19
forum: General Help
---

### Post by geovino on 2011-04-19
Update error today... Did a search but no info came up.

W: Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-l10n_12.0.732.0~svn20110409r81047-0ubuntu1~ucd1~lucid_all.deb](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/pool/main/c/chromium-browser/chromium-browser-l10n_12.0.732.0~svn20110409r81047-0ubuntu1~ucd1~lucid_all.deb)
  404  Not Found

Try again tomorrow?

running 10.04 32bit

---

### Post by Enigmapond on 2011-04-19
Maybe the server was busy. Usually you can try back in an hour or so and it will be fine. Unless this isn't the first time you've had this problem..I have the same PPA and my update just worked fine.

---

### Post by geovino on 2011-04-19
It's been awhile since I've got an update error. Though maybe because of it being version 10.04.

Thank you.

---

### Post by Krytarik on 2011-04-19
It seems like your local package database is outdated, try updating it before running the upgrade again, like with:
```
sudo apt-get update
```
Greetings.

---

### Post by geovino on 2011-04-19
> **Krytarik said:**
> It seems like your local package database is outdated, try updating it before running the upgrade again, like with:
```
sudo apt-get update
```
Greetings.

That's exactly what it needed! All is well now. Haven't used this laptop in a couple weeks.

Thanks :)

---

