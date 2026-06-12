---
title: "config files not reinstalling..."
date: 2011-05-11
forum: General Help
---

### Post by Xeneth on 2011-05-11
I mistakenly deleted /etc/apache2/port.conf, so I tried to reinstall the package with "apt-get", but nothing.  I dug myself in deeper by thinking a script skipped it because the directory was there, so I removed it completely.

After reinstalling using "apt-get install apache2", the folders came back, bot non  of the config files where there.  I am now lost.  How can I get them all back?

---

### Post by Xeneth on 2011-05-11
At the worse, I can put it on my laptop, then simply copy them over, but still looking for the answer.

---

### Post by sisco311 on 2011-05-11
According to dpkg /etc/apache2/ is provided by apache2.2-common:
```
dpkg -S /etc/apache2/
```

So purge it (this will remove the package and its config files), then re-install it:
```
sudo apt-get purge apache2.2-common
```
```
sudo apt-get install apache2.2-common
```

---

