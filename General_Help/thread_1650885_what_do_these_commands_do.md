---
title: "what do these commands do?"
date: 2010-12-22
forum: General Help
---

### Post by nrundy on 2010-12-22
Trying to get a brother printer working I went to Brother website and downloaded a driver. In the instructions its said to execute these commands before installing the driver. I did as instructed but in an effort to learn I'd like to know what these commands do? Why did I have to execute them?      Requirement     1. "sudo aa-complain cupsd" command is required before the installation.     2. "sudo mkdir /usr/share/cups/model" command (as it is) is required before the installation.

---

### Post by 3Miro on 2010-12-22
[http://man.he.net/man8/aa-complain](http://man.he.net/man8/aa-complain)

Apparently the first command turns off some security associated with the printers service (I think temporarily).

The second command creates a folder /usr/share/cups/model

---

### Post by sisco311 on 2010-12-22
If you are using cups >=1.3.9-2ubuntu6 (Ubuntu 9.10 or higher), then you don't have to change the enforcement mode. See: [lpbug]237256[/lpbug]

You can check the version of cups with:
```
apt-cache policy cups
```
and (re)set the enforcement mode to enforce with:
```
sudo aa-enforce cupsd
```

---

