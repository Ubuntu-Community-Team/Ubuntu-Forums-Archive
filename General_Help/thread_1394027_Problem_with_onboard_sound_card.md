---
title: "Problem with onboard sound card"
date: 2010-01-30
forum: General Help
---

### Post by Aramil on 2010-01-30
Hello,

I have a Dell Optiplex 755 running Ubuntu 8.04LTS.Yesterday after a shortcircuit of another device,after putting the power back on,I realised that Ubuntu did not recognize the onboard sound card (which is the only sound card on the computer).

I tried editing alsa-base.conf, reinstall alsa-base and all the need sound drivers but no progress.I checked the BIOS and the device is enabled.The device is also recognised by the lspci command.

My question is, can the sound card be dead but still recognizable by the system (at least in the lspci command).

P.S I tried 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

but none gave a solution...

---

### Post by smoka on 2010-01-30
I'd try booting to a Live CD first, and if the sound works in that, then you know it's something wrong with the installation, so at least that would discount a hardware issue.

---

