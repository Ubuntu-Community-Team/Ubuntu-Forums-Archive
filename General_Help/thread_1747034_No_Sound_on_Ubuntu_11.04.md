---
title: "No Sound on Ubuntu 11.04"
date: 2011-05-02
forum: General Help
---

### Post by Baharmur on 2011-05-02
Hi,
I have just upgraded Ubuntu to 11.04 and there is no sound, no audio...
Anyone knows how to solve this?
Thanks...

---

### Post by dino99 on 2011-05-02
got this issue after upgrading too, need to install ubuntu-restricted-extras from synaptic

---

### Post by Baharmur on 2011-05-02
I have installed ubuntu-restricted-extras, didn't work. Still no sound...

---

### Post by vaporx2 on 2011-05-02
I had a problem, if I install the drivers for my laptop ati radeon 5730, after I installed the driver, slow graphics,,, but if I did not install ati radeon driver, was light ...
can anyone help?

---

### Post by bravo sierra echo on 2011-05-02
Sorry if this sounds obvious, but have you checked the volume control?

Since I installed 11.04, it seems to set itself to "mute" on almost every restart.  I wish it would keep the setting and remain unmuted!

---

### Post by Baharmur on 2011-05-02
That was the first thing I thought of too. 
I have checked it. It is not mute.

---

### Post by mybunche on 2011-05-02
After a clean install of Ubuntu 11.04 I had no sound output on my Dell Latitude 2100. Note that I had sound when using the LiveCD.

Try this:
Goto System Settings then Startup Applications and untick PulseAudio Sound System KDE Routing Policy. Restart the computer.

That fixed it for me.

---

### Post by Baharmur on 2011-05-03
This didn't work either, but thanks for the reply...

---

### Post by Exodist on 2011-05-03
I am having sound issues also.
I am running a MSI 770 something with built in sound and NV 460 video.
Now I use the on board sound, at least the headphones jack in front works. 
The GF (NV460) sound I turn off, my monitor doesnt support HDMI sound.
I have tried every option on the list. The only thing that semi works is the ANALOG STEREO options, and those only work with the headphones. 
Now I just had sound working perfectly with Kubuntu 10.10, but wanted to go Ubu 11.04 to help with getting everything squared away before the LTS is released.

Well anyway, I disabled  KDE sound runtime also. But still only headphones work.
Not sure if the OP is having similar issues, so I thought I would throw in some more details. 

- Exo

---

### Post by leeishom on 2011-05-04
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


and then...

udo apt-get install linux-sound-base alsa-base alsa-utils

worked for me, using an intel chip.

---

### Post by Baharmur on 2011-05-04
Well, still nothing...
Thanks...

---

### Post by Baharmur on 2011-05-04
The problem was solved. I reinstalled every package containing alsa and asound and also apparently the packages bse-alsa and alsa-tools-gui was missing. I installed them too and the audio works fine...

---

### Post by Pyro_Dub on 2011-09-21
> **mybunche said:**
> After a clean install of Ubuntu 11.04 I had no sound output on my Dell Latitude 2100. Note that I had sound when using the LiveCD.

Try this:
Goto System Settings then Startup Applications and untick PulseAudio Sound System KDE Routing Policy. Restart the computer.

That fixed it for me.

I have a pavilion dv6809us and randomly one day the mute button turned on and wouldn't go away even though the computer said it was on full volume and doing this fixed everything.

---

