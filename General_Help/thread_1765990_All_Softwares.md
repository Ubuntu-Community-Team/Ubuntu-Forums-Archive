---
title: "All Softwares"
date: 2011-05-23
forum: General Help
---

### Post by rafi_ccj on 2011-05-23
I am new in Ubuntu linux. I want to know when i update my ubuntu where all software are kept . cause i dont wanna download these softwares again and again if i re install my ubuntu..........

---

### Post by linuxinstalledfromhdd on 2011-05-23
As long as you have properly installed Ubuntu, once you have installed application correctly it should remain there until you uninstall it.

Try using a walkthrough to get familiar with the way it works:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by matt_symes on 2011-05-23
Hi

> **rafi_ccj said:**
> I am new in Ubuntu linux. I want to know when i update my ubuntu where all software are kept . cause i dont wanna download these softwares again and again if i re install my ubuntu..........

When you download items using apt-get or synaptic they are kept in 

```
/var/cache/apt/archives/
```

You can backup that directory.

Kind regards

---

### Post by Telengard C64 on 2011-05-23
[Create backup of all installed packages using APTonCD in Ubuntu | Ubuntu Geek](http://www.ubuntugeek.com/create-backup-of-all-installed-packages-using-aptoncd-in-ubuntu.html)

```
sudo mkdir /backup
sudo sh -c 'dpkg --get-selections > /backup/installed-software.log'
```

HTH

---

