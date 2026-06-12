---
title: "PulseAudio stopped working with USB speakers; No sound"
date: 2009-11-02
forum: General Help
---

### Post by LucidStrike on 2009-11-02
The USB speakers I was using with my Karmic Koala Kubuntu setup suddenly stopped working, more or less. They produce sound fine enough when tested as 'USB Audio', but no applications seem to send sound directly to them in practice. PulseAudio, which used to send sound to the speakers stopped doing so. In testing, I can only hear PulseAudio through headphones (and presumably other outputs that aren't USB).

I sent in a [bug report]("https://answers.launchpad.net/ubuntu/+question/88020") and haven't really gotten any help yet.

Any help would be greatly appreciated. :D

---

### Post by LinuxBob on 2009-11-21
Same issue after upgrading to Karmic.  No sound from USB speakers that had previously worked fine in Jaunty.  I had pulse audio working in 9.04 switching streams, now cannot do that

---

### Post by elphaba on 2009-11-21
Maybe you should check to see if /etc/modprobe.d/alsa-base file has been modified on your system such that "usb snd audio" is entered with an "index=-2" or something/anything.  This would/might change the default for sound on your system and would affect playback, at least it did on mine.  Comment out any line for "usb snd audio" and reboot.

Whether or not your alsa-base file was modified, you should also (after you've rebooted if you modified the file above)
click on the pulseaudio applet (mine is in a tray at the top right of my screen)
next select volume control
Next select playback (confirm that your usb audio is on top, i.e. the default)
then adjust volume by sliding bar - this was the point where my speaker(s) began working properly

---

