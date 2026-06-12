---
title: "Ubuntu Reinstallation"
date: 2010-03-13
forum: General Help
---

### Post by rocket16 on 2010-03-13
Hello all. I had to reinstall Ubuntu 9.10 recently for a Python Problem. Now, I have several packages, massive ones like Wesnoth etc., left, those I collected from the cache of the broken OS. Now, after a fresh install, I do not wish to download all those packages again. I tried "sudo dpkg -i *.deb" command, but it says that there are several Broken packages. Now, if I simply put the deb files in my /var/cache/apt/archive directory, and try to reinstall those packages from the Internet, will those packages be downloaded again? Or, will they simply be used, since they are already present? Please help, since I do not wish to download all those massive packages again. Thanks.

---

### Post by Elfy on 2010-03-13
I have done that - you need to copy them as root and do an apt-get update and it should recognise them.

---

