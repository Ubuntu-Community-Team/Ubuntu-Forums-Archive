---
title: "apt-get update is giving error"
date: 2010-03-19
forum: General Help
---

### Post by saravana on 2010-03-19
Hi all,

i installed ubuntu9.10. when i try to update using 
sudo apt-get update   command, i am getting the following error.

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-proposed Release.gpg
  Cannot initiate the connection to in.archive.ubuntu.com:80 (2401:4800::111:91:91:4). - connect (101: Network is unreachable) [IP: 2401:4800::111:91:91:4 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_IN.bz2)  Cannot initiate the connection to in.archive.ubuntu.com:80 (2401:4800::111:91:91:4). - connect (101: Network is unreachable) [IP: 2401:4800::111:91:91:4 80]

please let me know how to resolve this?

---

### Post by Drenriza on 2010-03-19
Can you take a copy of your
/etc/apt/sources.list

and display it here?

use
```
gedit /etc/apt/sources.list
```
in the terminal.

---

