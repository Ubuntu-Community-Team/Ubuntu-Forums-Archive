---
title: "No sound in one profile"
date: 2011-03-06
forum: General Help
---

### Post by Dashiamo on 2011-03-06
Today I tried plugging in a microphone to my PC, to test if it was working I opened up the sound recorder that came with ubuntu and pressed record. When I clicked stop it popped up a continual error that I couldn't close, I force quit the sound recorder and since then I don't have sound on this profile. Ubuntu still looks like it's recognizing my sound card though.

Also I'm running Ubuntu 10.04 or 10.10 not sure (dunno how to check)


Just looked through the log file and found this whenever i log in:

pulseaudio[1886]: module-alsa-card.c: Failed to find a working profile.

pulseaudio[1886]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="0" name="pci-0000_02_00.1" card_name="alsa_card.pci-0000_02_00.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

---

