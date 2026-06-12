---
title: "I need really help with apache and now linux"
date: 2010-02-01
forum: General Help
---

### Post by aintour on 2010-02-01
i tried to uninstall apache mysql php5 because of some missconfiguration and install it again and now i have this error  messages. please help me i need to re install and install again.

on uninstall:
Could not get lock /var/cache/apt/archives/lock - open(11:Resource temporarily unavailable)
E: unable to lock the download directory


Please someone help me. I need fully uninstallation and installation from the beggining.

if i tried to remove it with purge command i get this error.
Could not get lock /var/cache/apt/archives/lock - open(11:Resource temporarily unavailable)
E: unable to lock the download directory

---

### Post by audiomick on 2010-02-01
It may be that the server is just offline for a while. You could try another source, or wait a while and see if it comes back.

---

### Post by aintour on 2010-02-01
If i tried to uninstall or install or everything around mysql and apach2 i get this error, so i need a clearly solution for uninstalling and installing again.

Could not get lock /var/cache/apt/archives/lock - open(11:Resource temporarily unavailable)
E: unable to lock the download directory


so something i did wrong or i deleted...

---

### Post by pirateghost on 2010-02-01
it means that the package manager is busy doing something else.  it is probably hung up on another process. reboot and try again.

---

### Post by aintour on 2010-02-01
i tried to reboot and....re install again but again the same problem.

---

### Post by junapp on 2010-02-01
what command are you using to install? Are you using 'sudo'?

---

### Post by aintour on 2010-02-02
yes i am using sudo apt-get install etc...

---

