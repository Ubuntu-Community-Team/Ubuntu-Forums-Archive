---
title: "No sound after realtex driver install"
date: 2011-07-10
forum: General Help
---

### Post by srisharan on 2011-07-10
Hello all,I wanted to try the realtek drivers for linux for a long time.So today I downloaded them and ran the installer.But I got an error 
```
./install: 48: alsaconf: not found

```

When I rebooted I found that my system lost my audio capabilities.So is there a way to either completely remove or properly install the realtek drivers to get my sound back.Thanks in advance.I am using natty by the way

---

### Post by Solanis on 2011-09-23
A little late in the reply but I've just gone through the same process myself.

I solved it by installing the latest ALSA drivers (which the Realtek drivers seem to be based on, based on the info they give). Read the info [here]("http://ubuntuforums.org/showthread.php?t=1681577") then grab the ALSA update script Temüjin provides. Fixed it for me.

With the script, note that there are three stages, so you need to read the output it gives when running it. Short version: run the script with the -d switch first (download), then the -c switch (compile) then the -i switch (install).

---

