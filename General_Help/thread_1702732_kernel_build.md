---
title: "kernel build"
date: 2011-03-08
forum: General Help
---

### Post by shekhar85 on 2011-03-08
Hi,

I was trying to build a linux based distribution, but I encountered the following problem:

When I run "make menuconfig" I get :

find vendors -mindepth 2 '(' -name .svn -prune ')' -o -type f -name Kconfig -print | sed 's:^:source ../:' > vendors/Kconfig
config/mkconfig > Kconfig
/bin/sh: config/mkconfig: Permission denied
make: *** [Kconfig] Error 126

I am using Ubuntu 10.10 to create the build.
I am running the build command as super user by doing sudo -i to get to the root terminal.

I was wondering why I was getting a "Permission denied" error?

Regards,
Shekhar

---

