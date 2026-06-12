---
title: "how to lock directry"
date: 2011-08-10
forum: General Help
---

### Post by jibawakee on 2011-08-10
Unable to lock directory /var/cache/apt/archives/
 


whenever i use sudo apt-get to install my apps in the terminal this pops up when its almost done downloading 


thanks

---

### Post by drs305 on 2011-08-10
It normally means another installation (APT) program is running, such as Synaptic, Update Manager, Software Center installation, etc.

Check the apps you normally use to install packages to see if they are running. If they are open, close them.

You can also check for running apps via the command line. Since installing requires root privileges, use the following command:

```
ps -u root
```
You can kill running apps from the command line with "sudo killall <appname>" but I would try rebooting first. I would recommend a reboot first, as it should shut down running apps in an orderly manner.

---

### Post by Habitual on 2011-08-10
```
lsof /var/cache/apt/archives/ | awk '{print $1}' | uniq
```
will also show you what's running out of that directory at the time.

---

### Post by papibe on 2011-08-10
Try what I say on your [other]("http://ubuntuforums.org/showthread.php?t=1822657") post.

---

