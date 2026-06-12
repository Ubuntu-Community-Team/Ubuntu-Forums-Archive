---
title: "No sound"
date: 2010-06-05
forum: General Help
---

### Post by Enrique101 on 2010-06-05
10.04 will not play sound. It's definitely a kernel issue and I am not the only one from what I read elsewhere. Prior to kernel 2.6.28 audio works on this Samsung Q1 Tablet PC. Any kernels from 2.6.28 onwards will not recognize my sound card and therefore won't play sound no matter what. I've proved it running different livecds (Suse, Mandriva, PCLOS, etc.) with kernels 2.6.25, 2.6.27, etc., all with audio. Now, how can I use/import a suitable kernel for Lucid Lynx 10.04 so that it will recognize my sound card (snd-hda-intel) on this Q1? Any comments would be much appreciated.

---

### Post by TheDesertDragon on 2010-06-05
Ubuntu's soundsetup can be imperfect.

Perhaps the only appropriate driver for your soundcard is an ALSA card, but Ubuntu uses PulseAudio.

PulseAudio is good and is very difficult to remove, but Ubuntu's setup of it is sometimes imperfect.

Check if the following things are done. If they aren't done, do them:

1)
Type sudo gedit /etc/asound.conf

If there is nothing in this file (ie. it doesn't exist) then add this:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

2)
Type
sudo gedit /etc/libao.conf

Search for the line
default_driver=pulse

If it isn't already there or if the file is empty, paste the line.

3)
Download the following packages by typing this into a terminal:
sudo apt-get install libflashsupport padevchooser pulseaudio-module-hal pulseaudio-module-x11

Restart your computer. Do you have sound?

---

### Post by Barafu Albino Cheetah on 2010-06-05
Using or not using pulseaudio does not make difference because pulseaudio uses alsa drivers. 
So 
1) install program called pavucontrol. Run it. Check you audio card is or is not there on "Output" tab. If it is, check it is not muted, that is the most popular problem. 
If it is not 
2) Check if kernel has your audio driver disabled. For this, install kernel sources, go to /usr/src/linux-kernel(your version) dir. type make menuconfig. 
There in device drivers look for audio drivers. There search for you audio card. This page will help [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
If it is not there at all, you are out of luck. May be this helps. [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)
If it is there, but checked out, then don't change anything! Close the terminal, killing the app, to not save anything. Carefully read about Ubuntu kernel configuration first, because it has a lot of hidden problems, unlike gentoo. Then enable the driver. 
Finally, if is is there and enabled, you problem has nothing to do with kernel version. 

PM me if this don't help, shall type more.

---

