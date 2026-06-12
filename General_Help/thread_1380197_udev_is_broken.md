---
title: "udev is broken"
date: 2010-01-13
forum: General Help
---

### Post by andypi on 2010-01-13
The udev package in my Ubuntu (karmic) distribution has somehow become broken. I've tried fixing it using synaptic and apt-get, but to no avail. My system currently won't shut down (presumably this is related...) and I also can't upgrade.

Can anyone tell me how to fix this? Below is what I get by trying to fix with apt-get:

[INDENT]sudo apt-get check -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
  consolekit: Breaks: udev (< 147) but 147~-6.1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies[/INDENT]

Thanks,

Andy

---

### Post by michy99 on 2010-01-13
Have you tired```
sudo dpkg --configure -a
```

---

### Post by andypi on 2010-01-13
Thanks, I just tried that but it doesn't seem to have worked:

sudo dpkg --configure -a
Setting up dbus (1.2.16-2) ...
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
update-rc.d: warning: /etc/init.d/dbus missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/sbin/runlevel: relocation error: /sbin/runlevel: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
start: relocation error: start: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
invoke-rc.d: initscript dbus, action "start" failed.
dpkg: error processing dbus (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of consolekit:
 consolekit depends on dbus (>= 1.1.2); however:
  Package dbus is not configured yet.
dpkg: error processing consolekit (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dbus
 consolekit

---

### Post by michy99 on 2010-01-13
Maybe this will work.```
sudo apt-get clean
sudo apt-get install --reinstall dbus consolekit
```

---

### Post by andypi on 2010-01-13
Still no :-(

```
sudo apt-get clean
sudo apt-get install --reinstall dbus consolekit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of dbus is not possible, it cannot be downloaded.
Reinstallation of consolekit is not possible, it cannot be downloaded.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  consolekit: Breaks: udev (< 147) but 147~-6.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I did also try "apt-get -f install", but got roughly the same as before.

---

### Post by andypi on 2010-01-13
OK. So eventually I tried running something like ```
sudo aptitude upgrade-complete
``` (can't remember exactly). It reinstalled lots of packages, and when it finished, synaptic no longer warned me of any broken packages. I was told I needed to restart my system. The system wouldn't restart when I told it to - it just logged out. I forced a shutdown, but now it won't reboot, and I'm currently running from a flash drive. Is there any way I can use the flash drive to repair the installation?

---

### Post by jahonen on 2010-01-29
Is there any new news on this one? I have the exact same problems. It may have something to do with all the errors for LSB that I suddenly got after the update.

I'm weary of trying anything too dramatic as I have the exact same symptoms as you and shutdown is not working (libc-issue) and I have a dreary feeling that if I touch this, it won't boot and it's my home NAS server with tons of stuff and services that my family uses all the time,

Regs, Jarkko

---

### Post by andypi on 2010-01-29
I'm afraid I ended up backing up, formatting and reinstalling. I needed to repartition anyway. Sorry, I don't suppose that will help. Good luck.

---

