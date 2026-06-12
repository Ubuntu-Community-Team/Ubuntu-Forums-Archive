---
title: "fglrx hangs on shutdown"
date: 2011-04-03
forum: General Help
---

### Post by naasking on 2011-04-03
I'm not 100% certain, but I'm fairly sure that fglrx is preventing clean shut downs. Hardware is an ASUS E-35M1-I Deluxe, so fairly new, and I'm running Ubuntu natty.

I couldn't find anything damning in the logs under /var/log, so I'm not sure where I can look to find the specific errors. All I know is that when I'm running with fglrx shutdown takes forever, as if it's waiting for the X server, and it just never shuts down cleanly, but when I run with the standard radeon driver everything shuts down quickly and cleanly.

Sometimes when I tried to execute a "service slim stop" or "service gdm stop", the whole system would hang, and needed a hard reset.

Any suggestions?

---

### Post by naasking on 2011-04-04
Bump.

---

### Post by cottfcfan on 2011-04-04
Someone correct me if i'm wrong, but as far as i'm aware AMD haven't yet released an FGLRX driver thats compatible to Natty!

---

### Post by naasking on 2011-04-04
The fglrx compatibility issues are supposedly fixed:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/709505](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/709505)

---

### Post by cottfcfan on 2011-04-04
If you check here people are still having problems.
[http://ubuntuforums.org/showthread.php?t=1719874](http://ubuntuforums.org/showthread.php?t=1719874)
Its unusual for fglrx to work properly, until after final release.

---

### Post by naasking on 2011-04-04
Not working is one thing, a hard lockup is another thing altogether. Everything else works perfectly otherwise, ie. hardware accelerated video in XBMC, accelerated 3D, etc. Besides, natty is needed for the drivers to support this brand new hardware.

Executing "sudo service slim stop", I get "slim is not responding to TERM signals". slim.log shows "unexpected signal 15", but slim and X are still running. No errors in the Xorg.0.log file. Slim no longer responds to input when switching to view the login screen, perhaps because it's trying to shut down.

Trying to kill slim manually has no effect, probably because it's already trying to shut down, but fglrx and/or X won't let it. This is probably what's preventing a clean shut down.

"kill -9" on slim and X do kill them, but certain kernel resources are clearly not reclaimed because switching to the X console, ie. alt-F7, produce a black screen and I can't get back to a regular tty console. System still responds to ctl-alt-delete reboot though (sometimes).

No adverse messages in the logs that I can see. If no one has any other ideas on how to proceed, I'll just file a bug.

---

### Post by MattKP on 2011-05-20
I have the same problem with an AMD RS780 chipset, ATI Radeon HD 4300. The system will not shutdown or reboot after login. It will however shutdown and reboot from gdm login screen.

---

### Post by MattKP on 2011-05-20
In addition, I've noticed a sharp decline in flash video performance that coincided with the shutdown/reboot issue.

---

