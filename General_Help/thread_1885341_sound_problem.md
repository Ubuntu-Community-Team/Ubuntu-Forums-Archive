---
title: "sound problem"
date: 2011-11-23
forum: General Help
---

### Post by kamildos on 2011-11-23
Hi, i install ubuntu 11.10 and the sound was working very well since i have done updates. Now, I have no sound at all. When i put my hearphone there is sound but its very bad . On windows 7 all is working well. Someone can help me pls ?

---

### Post by camaron1 on 2011-11-23
> **kamildos said:**
> Hi, i install ubuntu 11.10 and the sound was working very well since i have done updates. Now, I have no sound at all. When i put my hearphone there is sound but its very bad . On windows 7 all is working well. Someone can help me pls ?
 
 
Have a look at your sound preferencies which you can access from System Preferences or your Sound applet. Particularly check the sound card the your output.
 
Good luck

---

### Post by BC59 on 2011-11-23
From the guide:

If you get no sound with a fresh install, check that the sound levels are not set to zero. Click on the sound (speaker) icon on the panel, and then mixer. You may need to expand the dialog window to show labels. Ensure levels aren't set to zero, especially PCM.
PulseAudio
Sound in (K)Ubuntu is routed by Phonon either directly to your sound card or through the PulseAudio sound system. To use PulseAudio, you must install it. This can be done by installing the PulseAudio control modules (which will install pulseaudio as a dependency):
Install PulseAudio with the control modules:
sudo apt-get install pavucontrol paprefs
Although I no longer use it, in older versions of (K)Ubuntu I also (optionally) installed a system tray widget:
sudo apt-get install padevchooser
padevchooser
Some experimentation with the settings in
Menu -> System -> System Settings -> Multimedia
may be necessary to make sound on your system work properly.
Try setting PulseAudio as the first sound system if you are having troubles getting sound (even if you are using ALSA). If that doesn't work, try making it the last choice.
Some programs require ALSA sound and try to send sound directly through ALSA drivers. Check your program's preferences section to see if ALSA is selected. You may have to switch to PulseAudio (or even OSSound) if you can't get sound.

---

### Post by kamildos on 2011-11-25
Thanks for the help but i already verify those option. Sometime when i start ubuntu there is sound  Personnaly i think its a update that bring me this problem

---

### Post by raja.genupula on 2011-11-25
[http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

