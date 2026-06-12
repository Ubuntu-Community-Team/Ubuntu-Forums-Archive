---
title: "ALC880 problem"
date: 2006-04-19
forum: General Help
---

### Post by _teo_ on 2006-04-19
Hi, I installed on my machine 64-bit Breeze. I had problem while installing it with the sound chip - ALC880. It was freezing at hotplug subsystem. My solution is that I disabled it in BIOS and when done with installation I blacklisted both snd_hda_intel and snd_hda_codec in /etc/hotplug/blacklist as described in [this thread]("http://ubuntuforums.org/showthread.php?t=132156").

Later I found [this reply]("http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html") to the same problem. My question is whether this solution will work without side effects with 64-bit version.

Thanks in advance!

---

### Post by _teo_ on 2006-04-21
Well, either nobody knows or those who know are shy. ;) 

Then I have to try it out. My problem is that I am relatively new to Linux world and if something goes wrong I have to reinstall the whole system. :-k

---

### Post by _teo_ on 2006-04-21
Great! The package alsa-source_1.0.10-3_all.deb isn't there... ](*,) Any ideas?

---

