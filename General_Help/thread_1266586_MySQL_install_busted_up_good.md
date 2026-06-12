---
title: "MySQL install busted up good"
date: 2009-09-14
forum: General Help
---

### Post by wesg on 2009-09-14
I had mysql running nicely on my 9.04 CLI server, but then I installed mythTV. Strangely, since then mysql has not worked. I've tried many of the commands to remove it, but each time I try to reinstall, I get the following text: 
```

Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas as to how I can get my server running?

---

### Post by utnubuuser on 2009-09-14
that's not just an issue of apt-get not being up to date?

As in sudo apt-get update?

sudo apt-get --fix-broken?

---

### Post by wesg on 2009-09-14
Unfortunately that didn't quite work, but at this point I have the mysql packages uninstalled.

The problem now is that I can't uninstall the package again... I still get that same error. I cleared the cache and downloaded the packages again, but nothing has worked.

---

### Post by wesg on 2009-09-14
Not quite sure how, but I finagled 5.1.31 back onto the system... Back in business now.

---

