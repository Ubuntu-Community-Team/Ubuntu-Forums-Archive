---
title: "bash: make: command not found"
date: 2006-01-26
forum: General Help
---

### Post by utnubu! on 2006-01-26
bash: make: command not found

why is this command not found? and how should i fix this?

---

### Post by Lambert on 2006-01-26
You need to install the package build-essential from the install cd or repos as make is not installed by default on ubuntu.

---

### Post by public_void on 2006-01-26
If you compiling from source, then check the lines at the end after doing the ./configure command. It will tell you of any problems that may have occured. It could be that your missing some dependencies.

---

### Post by utnubu! on 2006-01-26
i fixed the problem by installing build-essentials but i have another problem

i am installing softmac(trying to get my airport express working) but when i enter the make command i get this error

make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd`/net/ieee80211 CONFIG_IEEE80211=m CONFIG_IEEE80211_CRYPT_WEP=m CONFIG_IEEE80211_CRYPT_CCMP=m CONFIG_IEEE80211_CRYPT_TKIP=m CC="gcc -I`pwd`/include" modules
make: *** /lib/modules/2.6.15.1/build: No such file or directory.  Stop.
make: *** [modules] Error 2

---

