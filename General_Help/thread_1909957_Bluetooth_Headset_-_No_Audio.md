---
title: "Bluetooth Headset - No Audio"
date: 2012-01-16
forum: General Help
---

### Post by BrokenKingpin on 2012-01-16
I bought a bluetooth headset/headphones and I am able to pair it to my netbook (running Xubuntu 11.10), but the audio still comes out of the netbook speakers, not the headset. I also tried under Kubuntu with the same issue.

The headset is a Sony DR-BT101/BLK. I know the headset is fine because it works perfectly with my Android phone (Samsung Gio).

Does anyone know how to get these running under *buntu? It also has volume and media controls right on the headphones that I would also like to get working. Maybe I just need to switch the output in pulseaudio, I just don't know how to do that. Any help would be great, thanks.

---

### Post by BrokenKingpin on 2012-01-16
I have figured it out. I had to install pulseaudio-module-bluetooth. After this it picked it up as a headset fine. I installed pavucontrol to configure the headset to A2DP and set it as the default output.

---

