---
title: "Lost all PNG images among other formats after trying to install gimp 2.8"
date: 2012-05-03
forum: General Help
---

### Post by flyingfisch on 2012-05-03
I tried to install gimp 2.8 this way:

```

sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update
sudo apt-get install gimp

```

It had some kind of error and automatically logged me out. My login screen background was not displayed. I rebooted. When I try to save my screenshot to show you what it looks like I get "PNG format not supported". 

What happened? Can I fix this?

---

### Post by dniMretsaM on 2012-05-03
First thing you should do is remove that PPA. It will be in /etc/apt/sources.list.d/. The you can run:
```
sudo apt-get update && sudo apt-get install gimp
```

That might help. If not, post back with the output of the install command.

---

### Post by flyingfisch on 2012-05-03
I just fixed it by opening update manager and doing a partial upgrade, then removing the ppa, then purging gimp, then installing the bad dependencies, and then did *sudo apt-get install gimp*. It worked!

---

### Post by philinux on 2012-05-03
> **flyingfisch said:**
> I just fixed it by opening update manager and doing a partial upgrade, then removing the ppa, then purging gimp, then installing the bad dependencies, and then did *sudo apt-get install gimp*. It worked!

I'm going to try the ppa tomoz on 12.04. I think it should have no dependency problems. But who knows.

---

### Post by dniMretsaM on 2012-05-03
I just compiled it. Really easy. Like 4 commands and your done. Not for everyone, I guess. Anyway, glad you solved the issue!

---

