---
title: "How to use Clamscan on Windows Partition?"
date: 2012-03-15
forum: General Help
---

### Post by miasmablk on 2012-03-15
this is what im doing currently mount the windows partition i want to use

```
sudo mount /dev/sda1 /media/windows
```the run a recursive scan on said partition VIA

```
sudo clamscan -r /media/windows
```but what im wondering is how to utilize clamscan to move an infected file to a different directory or how to remove an infected file. as all im doing so far seems to detect in fected files?

i found this but i'm still confused exactly as to how to execute the commands:confused:
[http://linux.die.net/man/1/clamscan](http://linux.die.net/man/1/clamscan)

---

### Post by miasmablk on 2012-03-16
lol seems i always answer my own questions on here.

sudo mkdir /home/user/infected

sudo mount /dev/sda2 /media/windows

sudo freshclam

sudo clamscan -r --move=/home/user/infected /media/windows

thanks anyways.

---

### Post by Mark Phelps on 2012-03-18
ClamAV is only one of many AV products, and not one I have used.

If you really want to run AV products on MS Windows, but don't want to purchase anything, consider the following three options:
1) Microsoft Security Essentials -- FREE from MS and not bad
2) Kaspersky Rescue CD -- FREE ISO image download, runs their AV product
3) Avira CD -- similar to Kaspersky

---

### Post by miasmablk on 2012-03-19
actually i mostly use this for pc's where the malware/ virus infection has disabled the antivirus and firewall in windows and "safe mode" also prove ineffective in removing the infections.. p.s. love security essentials run it on all my windows boxes. free and lightweight ;)

---

