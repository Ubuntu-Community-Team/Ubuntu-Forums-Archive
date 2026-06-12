---
title: "32-bit vs. 64-bit Linux"
date: 2010-02-09
forum: General Help
---

### Post by denny8569 on 2010-02-09
I have an AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ and I'm currently checking out Ubuntu 9.04 64-bit, but as expected I'm running into a few hiccups here and there with 64-bit. For example, I had a 64-bit Flash plugin (pre-release) from Adobe running fine, but it appears it has since been replaced with a 32-bit version from the repos. Grrr. Thinking about going back to 32-bit already... :mrgreen:

On this computer I'll probably play around with emulators a little, but mostly it's used for web, email, office apps, a UPnP DLNA server for the PS3(s), etc.

---

### Post by zvacet on 2010-02-09
If you have problem with 64 bit version you can install 32 version.Even with 32 you can use more then 4GB of ram if you install linux-generic-pae kernel from synaptic.

---

### Post by lovinglinux on 2010-02-09
Remove any 32bit flash plugins with this:

```
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get install flashplugin-nonfree
```

Remove *libflashplayer.so* if it is present under ~/.mozilla/plugins

Then install the 64bit by following [this](http://ubuntuforums.org/showthread.php?t=1358591).

---

