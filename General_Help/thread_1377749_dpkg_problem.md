---
title: "dpkg problem"
date: 2010-01-10
forum: General Help
---

### Post by Ganesho on 2010-01-10
I am not able to update at all. Update manager returned an error reading

Preconfiguring packages ...
/usr/bin/dpkg: 1: Syntax error: ")" unexpected
E: Sub-process /usr/bin/dpkg returned an error code (2)

i get the same error if i update in a terminal or from Synaptic Package Manager. Thank you very much in advance.

---

### Post by michy99 on 2010-01-10
Try this:```
sudo dpkg --configure -a
```

---

### Post by Ganesho on 2010-01-10
The command

sudo dpkg --configure -a 

returns to the same error

/usr/bin/dpkg: 1: Syntax error: ")" unexpected

---

### Post by michy99 on 2010-01-10
Try this then:```
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
```

EDIT: forgot the 'sudo'

---

### Post by Ganesho on 2010-01-10
Thank you for your quick reply and your suggestions. This fix made it possible to run sudo apt-get update but as soon as i tried to apt-get upgrade i get the same error message again. This also happens if i try to use the Synaptic Package Manager or if i try to install the suggested security upgrades with Update Manager. The error message remains the same. 

Preconfiguring packages ...
/usr/bin/dpkg: 1: Syntax error: ")" unexpected
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by michy99 on 2010-01-10
Apparently there is a particular package that is causing the problem. Have you added any third party repositories? If so, try disabling all of them and see if updating works. If it does, then enable the other repositories one at a time and try to update until you find which one is causing the problem.

---

### Post by Ganesho on 2010-01-10
Thanks again for your help. I removed a couple sources i had added and re-enabled them one by one running the Update Manager with each one of them. This has cleared up the backlog on security and suggested updates. I am able to run apt-get update without a problem and the system appears to be up to date. I do not have many software sources enabled and the only change i had made recently was to add the launchpad.net/chromium-daily ppa. However if i run:

 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
26 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
/usr/bin/dpkg: 1: Syntax error: ")" unexpected
E: Sub-process /usr/bin/dpkg returned an error code (2)

I am still getting this error message. Thanks again for your help.

---

### Post by Ganesho on 2010-01-14
Can anybody help me with this. I still have this error message saying:

/usr/bin/dpkg: 1: Syntax error: ")" unexpected

but i have no idea what is causing it. I am not able to install anything and i get the same error if i try to use the Synaptic Package Manager. Thank you for your help.

---

### Post by Ganesho on 2010-01-16
Thank you all for your help with Ubuntu.

---

