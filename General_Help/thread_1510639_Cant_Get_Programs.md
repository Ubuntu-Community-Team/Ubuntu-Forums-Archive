---
title: "Cant Get Programs"
date: 2010-06-15
forum: General Help
---

### Post by Chad Olson on 2010-06-15
Every time I try to install a program with get free programs it won't let me install them. I get a message saying that the software is from an untrusted source but it says it for every program I try to download Is their a security setting I have to change somewhere.

---

### Post by oldos2er on 2010-06-15
Can you run this command in a terminal, and post the output here? ```
sudo apt-get update && sudo apt-get safe-upgrade
```

---

### Post by Chad Olson on 2010-06-15
Fetched 756B in 24s (31B/s)
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
E: Invalid operation safe-upgrade
chad@chad-desktop:~$

---

### Post by oldos2er on 2010-06-16
Run this command in a terminal ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
then retry ```
sudo apt-get update && sudo apt-get safe-upgrade
```

---

### Post by Chad Olson on 2010-06-16
Got it now thanks

---

