---
title: "Making a command permanent..."
date: 2010-05-20
forum: General Help
---

### Post by Linuxperiment on 2010-05-20
[http://ubuntuforums.org/showthread.php?t=961324](http://ubuntuforums.org/showthread.php?t=961324)

In this link, the last poster describes a way to disable tap click which I find VERY useful, but the thing is, after I reboot it goes away. Is there anyway to make this command permanent?

---

### Post by mikewhatever on 2010-05-20
You could try adding the command to /etc/rc.local. No need for 'sudo' there, just the command itself.

---

### Post by patchwork on 2010-05-20
I don't have a Sentelic touchpad, but there may be an option in gconf-editor like there is for the Synaptic touchpads:

```
gconf-editor
```
Desktop > Applications > Peripherals > Touchpad > Tap to click

---

