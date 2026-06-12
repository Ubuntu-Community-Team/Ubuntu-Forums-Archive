---
title: "consistent default cound card with no errors"
date: 2010-10-05
forum: General Help
---

### Post by kaligus on 2010-10-05
I have two sound cards so that I can do some regular streaming/shoutcasting with the ability to have my headset be just related to the broadcasting and use two mic inputs.  I have been unable to reliably set the default sound card since installing an otherwise fully functional card.

Both cards work fully (as long as pulse is not brought into the picture) the *only* problem I have a strong desire to fix is the random order of the cards.  Making skype work would be bonus but not going to cry if I never fix that.

I removed as much of pulse as possible because it has hated my onboard sound card since 8.10 or 9.04 this made everything work correctly until adding the second sound card.  

```
bigwill:[20101005.0715]will@~ :: uname -a
Linux bigwill 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux
``````
(random order of devices each boot)
bigwill:[20101005.0714]will@~ :: cat /proc/asound/modules
 0 snd_hda_intel  ## needs to be 1
 1 snd_usb_audio
 2 snd_ens1371    ## needs to be 0
```I tried pulse again with 10.04 and it still argues with the hda_intel and in a new development also has issues with jack and/or IDJC which make the entire audio system unusable (everything sounds like space aliens have taken over and errors are thrown often enough that I rebooted and uninstalled pulse again moments later, too many problems with pulse over 2 years to waste time trying to make that boat anchor (on my machine) work.

I have changed /etc/modprobe.d/alsa-base.conf to add the following line in several locations, top, middle, bottom of the file (top = after the auto aliases | middle = anywhere not top or bottom | bottom = last line of the alsa-base.conf).

```
options snd_hda_intel index=1
```This will randomly work as expected or fail to recognize one or the other card at all on boot and throw a random one of several errors which always result in the question:
"should I remove <random device>" 
Most commonly the analog front side of the onboard intel card (the most important device), sometimes the ensoniq or digital/rear hda devices.

```

bigwill:[20101005.0717]will@~ :: cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [U0x46d0x9a4    ]: USB-Audio - USB Device 0x46d:0x9a4
                      USB Device 0x46d:0x9a4 at usb-0000:00:12.2-2, high speed
 2 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xca00, irq 21

```I have edited /etc/asound.conf and ~/.asoundrc to
```
pcm.!default {
    type hw
    card AudioPCI
}
ctl.!default {
    type hw
    card AudioPCI
}
```

This seems to fail more often than editing the modprobe order with the same "remove <device or feature> question as the result.

In the end I still end up booting several times until I get no errors and the correct order of the cards.

Any new ideas or theories?

---

### Post by kaligus on 2010-10-08
bump for any ideas at all??

---

### Post by kaligus on 2010-10-13
last bump before I upgrade to 10.10.

---

