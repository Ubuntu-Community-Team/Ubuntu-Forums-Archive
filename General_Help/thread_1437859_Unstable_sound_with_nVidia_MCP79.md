---
title: "Unstable sound with nVidia MCP79"
date: 2010-03-24
forum: General Help
---

### Post by msp3k on 2010-03-24
I have a 24" aluminium mac (model iMac9,1) with an nVidia MCP79 audio card.  I can get the sound to work, but it's not stable.  I can make it degrade into digital static in usually less than 60 seconds by doing the following:

1) Open a terminal window and type: while true; do echo '^G'; sleep 1; done
    (Where ^G = control-v control-g)
2) Play a youtube video (so the OS must mix two sound sources)
3) Adjust volume up and down

I have tried the following:
1) With the stock 2.6.31-20-generic kernel (alsa 1.0.20):
1.1) option snd-hda-intel=mb5
1.2) option snd-hda-intel=imac24
1.3) option snd-hda-intel=mac24
1.4) option snd-hda-intel=mbp3
1.5) option snd-hda-intel=mb31
2) Tried 1.* w/ linux-backports-modules-alsa-karmic-generic
3) Tried 1.* w/ alsa-driver-1.0.22.1 compiled from source

Is there anything else I can try?  All ideas welcomed w/ open arms -- I'm getting desperate.

Thanks,

Michael

---

