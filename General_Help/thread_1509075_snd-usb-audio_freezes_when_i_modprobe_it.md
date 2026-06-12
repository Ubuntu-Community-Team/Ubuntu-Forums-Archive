---
title: "snd-usb-audio freezes when i modprobe it"
date: 2010-06-13
forum: General Help
---

### Post by macramole on 2010-06-13
Hi,

I was mixing some stuff with Ardour when it seems I suddenly kicked some wire or something. Thing is, my whole system crashed and when i reboot I can't get my usb card working. When I ```
#alsa reload
``` the command freezes and if I ```
$ps ax | grep modprobe
``` I can see "modprobe snd-usb-audio" but can't kill it.

I tried with a live cd and windows and the card is doing fine.. i think it must be some configuration setting or something..

any idea ?

---

### Post by macramole on 2010-06-20
:lolflag:

the answer was

```

#dpkg --purge --force-depends alsa-base alsa-tools alsa-utils
#aptitude install alsa-base alsa-tools alsa-utils

```

one could also 

```

#aptitude purge alsa-base alsa-tools alsa-utils
#aptitude install alsa-base alsa-tools alsa-utils

```

but this way aptitude will want to uninstall packages depending on alsa as well (including ubuntu-desktop :|)

I've rebooted between one command and the other but I don't know if that's mandatory

next step: make openframeworks work correctly under linux :(

cheers you all !

---

