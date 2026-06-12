---
title: "Adept giving weird error during installations and uninstallations (Dapper)"
date: 2006-05-03
forum: General Help
---

### Post by Gijith on 2006-05-03
Hello,

I've been running Dapper for a few weeks and this problem only began a few days ago. Whenever I install, upgrade or uninstall anything using Adept (I haven't noticed this problem using apt-get from CM), I get an error. Everything downloads fine, but about midway through the actual installation/replacement/removal process, I always get:

!!! There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages.

However, once I click OK, the process completes, the app is installed and seems to work perfectly. So, as far as I can tell, this error seems pretty meaningless. But I have no idea why it's there and I'd like to get rid of it.

Any suggestions?
Thanks a bunch!

---

### Post by ltmon on 2006-05-03
Dapper has been doing this trick intermitently since I started using it a month or so ago.  I think it's a known bug, and it's been getting better.

To be on the safe side I run a:
```

sudo apt-get upgrade

```
after every time this happens.

L.

---

