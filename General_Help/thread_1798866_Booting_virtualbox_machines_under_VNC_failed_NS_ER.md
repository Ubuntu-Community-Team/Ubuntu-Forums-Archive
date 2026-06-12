---
title: "Booting virtualbox machines under VNC failed NS_ERROR_FAILURE"
date: 2011-07-06
forum: General Help
---

### Post by bonuswhore on 2011-07-06
I have ubuntu 11.04 with virtualbox installed.  I have some old vmware virtual machines on an NTFS partition that I am able to successfully boot with virtualbox at my ubuntu desktop

however, when I vnc into my desktop from a remote location and start up virtualbox and try to boot my virutal machines, I get: > Failed to open a session for virtual machine.. the virtual machine has terminated unexpectedly during startup with exit code 0.

result code NS_ERROR_FAILURE 0x80004005
component: MACHINE
interface: IMACHINE
from googling this some people have indicated this means my username is not in the virtualbox user group, but I am logging in with the same username over vnc as I do when sitting at the machine where virtualbox works fine.  the directory the machines are on is mounted, not sure why I can't boot them

what else could be causing my problem? has anyone ever setup vnc4server on ubuntu and got virtualbox working?

---

### Post by bonuswhore on 2011-07-08
this is still stumping me..i went to system->administration-> users and groups and edited my username and checked the vboxusers group.  however I still get the same error when booting any virtual machine

---

### Post by wildmanne39 on 2011-07-09
> **bonuswhore said:**
> this is still stumping me..i went to system->administration-> users and groups and edited my username and checked the vboxusers group.  however I still get the same error when booting any virtual machineHi, have you tried virtualbox.org and click on there forum and post the question there? They are not as friendly over there but they deal only with virtualbox issues.

---

