---
title: "sudo apt-get install chromium - 0 upgraded, 0 newly installed, 0 to remove and 0 not"
date: 2010-10-10
forum: General Help
---

### Post by nospampleasemam on 2010-10-10
ran sudo apt-get install chromium, it seemed to install, i closed terminal, couldnt find it under apps, ran the command again, and am now getting this?

:-$ sudo apt-get install chromium
chromium is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

any help is appreciated!

---

### Post by andrewthomas on 2010-10-10
Wrong package name.

```
sudo apt-get install chromium-browser
```

---

### Post by sanderj on 2010-10-10
> **nospampleasemam said:**
> ran sudo apt-get install chromium, it seemed to install, i closed terminal, couldnt find it under apps, ran the command again, and am now getting this?

:-$ sudo apt-get install chromium
chromium is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

any help is appreciated!


The package "chromium" is a "fast paced, arcade-style, scrolling space shooter". It's not the browser. 

I think you want the browser. See [https://launchpad.net/chromium-project](https://launchpad.net/chromium-project) for an overview of possible Chromium browser versions.

I use the Beta version, see [https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta) for instructions how to install.

---

### Post by nospampleasemam on 2010-10-10
wow do i feel silly. thank you.

---

