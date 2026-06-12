---
title: "How to pass alsa options?"
date: 2004-10-22
forum: General Help
---

### Post by nuopus on 2004-10-22
Okay I just switched to Ubuntu from Gentoo and am trying to pass options to the sound module. Doend DOES work on my laptop but the volume is controlled through the PCM2 mixer.

In order to fix this I usually just add ac97_quirk=1 to a file that is added to modules.conf. 

Now here is the problem ... I found the file /etc/modutils/alsa-bas and tried adding options snd-intel8x0 ac97_clock=0 ac97_quirk=1 enable=1 index=0 joystick=0 to it so my sound works perfectly. What I noticed is that hotplug sets up the sound card and that is not used.

I even disabled pci hotplug and set the sound up manually and that actually worked but other things fail to work because I have disabled hotplug.

What file can I edit to tell hotplug to use my alsa options? Or should I just disable hotplug and configure everything else manually?

---

### Post by iwasbiggs on 2004-10-22
You can probably solve this by blacklisting the module in hotplug then manually load it later with your own options.

I added a few lines to /etc/hotplug/blacklist with the names of the modules I don't want to load.

---

### Post by nuopus on 2004-10-23
[QUOTE=iwasbiggs]You can probably solve this by blacklisting the module in hotplug then manually load it later with your own options.

I added a few lines to /etc/hotplug/blacklist with the names of the modules I don't want to load.[/QUOTE]

bahh what I was doing worked. I just misspelled the module name! LOL

---

