---
title: "Error: Must run as root"
date: 2011-04-30
forum: General Help
---

### Post by ChaosChris2009 on 2011-04-30
[CENTER]I'm on Natty, and I attempted to install BatteryStatus via Terminal

This is the command I ran: ```
add-apt-repository ppa:iaz/battery-status
```

Yet it gives me the error: ```
Error: Must run as root
```

Please help me, I really wish to install BatteryStatus.[/CENTER]

---

### Post by WorMzy on 2011-04-30
Use sudo.

```
sudo add-apt-repository ppa:iaz/battery-status
```

---

### Post by ChaosChris2009 on 2011-04-30
> **WorMzy said:**
> Use sudo.

```
sudo add-apt-repository ppa:iaz/battery-status
```

It gives back this when I run it

```
chrisv@chris:~$ sudo add-apt-repository ppa:iaz/battery-status
[sudo] password for chrisv: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 28FED23C44FB7ED6EBEDEF6B90DCEB7B6E7F922F
gpg: requesting key 6E7F922F from hkp server keyserver.ubuntu.com
gpg: key 6E7F922F: "Launchpad PPA for Ivan Zorin" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
chrisv@chris:~$ ^C
chrisv@chris:~$ 



```

---

### Post by WorMzy on 2011-04-30
You already have that PPA added as a software source. You can't add it again.

---

### Post by ChaosChris2009 on 2011-04-30
> **WorMzy said:**
> You already have that PPA added as a software source. You can't add it again.

So what I can do install this then? 

I've checked my sources, but I'm still encountering issues when trying to install BatteryStatus.

---

### Post by WorMzy on 2011-04-30
What can you do to install what?

```
sudo apt-get update && sudo apt-get install <package name>
```

---

