---
title: "kernel 3.2.0-27: No audio"
date: 2012-07-24
forum: General Help
---

### Post by BrumlePostmann on 2012-07-24
Todays update were mostly the kernel update 3.2.0-27, after I'd had no audio. Alsa mixer came up with the controls were they used to be, but the speakers were silent. Booted the previous version 3.2.0-26, and the audio were ok again. Looked in the syslog and dmesg, but could not see anything that I'd could relate to audio problems. Should I'd make an bugreport for this? If so, I'd wondering what information is adviced to include, I'd have no idea what's about with the kernel.

By the way, I'd have thrown out pulseaudio for alsa. After my computer have been running for a day or so, the audio began to stutter. Were advised to switch to alsa, and that seems to have solved the problem.

---

### Post by BrumlePostmann on 2012-07-25
Audio are back, running on kernel 3.2.0-27, monitors are also back into service. It was'nt the kernel, it was me trying to solve that Unity responding wery slowly problem by installing "proprietary drivers". Installation stopped with nvidia_96 not found, and seems to have been rolled back. It had not rolled back, the whole installation were corrupted as it hampered video and audio as well, but it needed an reboot just to complete the damage, which caused the kernel to be blamed. Strangely it helped to boot 3.2.0-26 kernel, but I'd not care. 

Ubuntu 12.04 were freshly installed and no data were lost, because I'd has a spare hard drive.

close case

---

