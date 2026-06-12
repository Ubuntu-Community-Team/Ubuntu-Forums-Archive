---
title: "Adobe Air installation on 12.04 fails"
date: 2012-05-11
forum: General Help
---

### Post by ELMIT on 2012-05-11
./AdobeAIRInstaller.bin

Adobe AIR could not be installed. Install either Gnome Keyring or KDE KWallet before installing Adobe AIR.

I have Seahorse installed and it is working.

---

### Post by Primefalcon on 2012-05-11
> **ELMIT said:**
> ./AdobeAIRInstaller.bin

Adobe AIR could not be installed. Install either Gnome Keyring or KDE KWallet before installing Adobe AIR.

I have Seahorse installed and it is working.
try installing it with ```
sudo ./AdobeAirInstaller.bin
```

---

### Post by gmehn on 2012-05-14
Try:

sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

---

### Post by ELMIT on 2012-05-14
gmehn, ... that worked, .... thanks!

Unfortunately Adobe Air will not anymore developed for Linux,....

---

### Post by 0n1m3 on 2013-04-23
Yeah, that works.

---

