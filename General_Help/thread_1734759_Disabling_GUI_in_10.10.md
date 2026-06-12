---
title: "Disabling GUI in 10.10"
date: 2011-04-20
forum: General Help
---

### Post by AI52487963 on 2011-04-20
I'm running Ubuntu 10.10 in VirtualBox on Win7 and wanted to disable the GUI.

So I followed the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=1607830") to try and get 10.10 to boot straight to a terminal without any of the GUI fuss, but it gets stuck at the "Checking battery state" stage.

Here's the output on the screen from where the lockdown occurs:

```
...

* Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox    [ok]

*Setting sensors limits     [ok]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
*(red) PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
*Enabling additional executable binary formats binfmt-support     [ok]
*Checking battery state...     [ok]
_
```Anyone know how to get this to un-stick? 

I'm on an Acer Aspire 5742 if that makes any difference.

---

### Post by ttshivers on 2011-04-20
You might want to take a look at this [http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/]("http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/") or this one [http://ubuntuforums.org/showthread.php?t=694605]("http://ubuntuforums.org/showthread.php?t=694605")

---

### Post by AI52487963 on 2011-04-20
> **ttshivers said:**
> You might want to take a look at this [http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/) or this one [http://ubuntuforums.org/showthread.php?t=694605](http://ubuntuforums.org/showthread.php?t=694605)

Actually the problem seems to have resolved itself. I just restarted the virtual machine a couple times and it boots directly to terminal now with no GUI. Thanks for the links, though!

---

### Post by AI52487963 on 2011-04-20
Me and my big mouth. It was working for a mintue there but now it's hung up again. Same issue as listed in OP. 

I still had the .iso loaded in the virtualbox and when I tried restarting from the hang, it would go to the install GUI. I removed the loaded .iso and the virtualbox booted the GUI-less ubuntu straight to the login without getting hung up on the battery state. 

I wanted to make sure it was totally working, so this time, without the .iso loaded, I rebooted, but got back to the same battery error.

Edit: just went back into recovery mode and undid the "fix" from the post I linked to in OP. Will try your method next...

---

