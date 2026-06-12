---
title: "Disable boot menu timeout"
date: 2011-10-27
forum: General Help
---

### Post by SkyeFerret on 2011-10-27
I have Win7 and Ubuntu 11.10 installed on my desktop. Prior to upgrading from 11.04, the boot menu *did* have a timeout, but after a while, it disabled itself. Now, the timer is back. How do I disable it?

(It's also got Ubuntu set as default OS, how do I change that to Windows? I use Windows more on this machine)

---

### Post by ajgreeny on 2011-10-27
These two links may help you:-
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") 
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by raja.genupula on 2011-10-27
> **SkyeFerret said:**
> I have Win7 and Ubuntu 11.10 installed on my desktop. Prior to upgrading from 11.04, the boot menu *did* have a timeout, but after a while, it disabled itself. Now, the timer is back. How do I disable it?

(It's also got Ubuntu set as default OS, how do I change that to Windows? I use Windows more on this machine)

Hi Man

install this 

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

after installing open it from the dash by typing its name and then click at preference.

All the best man

---

### Post by SkyeFerret on 2011-10-27
Thanks guys. <3 I'll try that out.

---

