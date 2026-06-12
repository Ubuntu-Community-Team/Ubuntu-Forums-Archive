---
title: "Package Dependency Not Installable"
date: 2010-07-09
forum: General Help
---

### Post by Rawrmage on 2010-07-09
Hi, I was attempting to install the package 'gnustep-devel', but the package 'gorm.app' which gnustep-devel depends on is not available. I've checked in Synaptic's Settings->Repositories and I have all repositories enabled, and the package is available via a Debian repository...  I'm pretty sure that there's a better place to report it than here, but I don't know where that is... Thank you!

---

### Post by mikewhatever on 2010-07-09
Have you tried installing gorm.app separately, ie,
sudo apt-get install gorm.app
?

---

### Post by Rawrmage on 2010-07-09
It isn't available... apt-get says that it's referred to, but not available, like I said. The exact error is:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gorm.app is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gorm.app has no installation candidate

```
I can get it at [http://packages.debian.org/stable/devel/gorm.app]("http://packages.debian.org/stable/devel/gorm.app") but the question I have is where I can go to try to get the problem (depended on but not available) remedied.

---

### Post by happyhamster on 2010-07-09
Bugreport:
[https://bugs.launchpad.net/ubuntu/+source/meta-gnustep/+bug/579735](https://bugs.launchpad.net/ubuntu/+source/meta-gnustep/+bug/579735)

Also see:
[http://thelinuxexperiment.com/tag/gorm-app/](http://thelinuxexperiment.com/tag/gorm-app/)

Good luck.

---

### Post by Rawrmage on 2010-07-09
Thank you very much, that is exactly what I was looking for.

---

