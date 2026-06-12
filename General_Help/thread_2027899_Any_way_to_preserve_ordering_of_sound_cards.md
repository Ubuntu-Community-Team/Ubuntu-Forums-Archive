---
title: "Any way to preserve ordering of sound cards?"
date: 2012-07-17
forum: General Help
---

### Post by cbraxton on 2012-07-17
My Xubuntu 12.04 system has both a Sound Blaster audio card and HDMI audio output. (I don't use the HDMI.) What is happening is that at boot time the Sound Blaster will sometimes be assigned as card "0" and sometimes as card "1" randomly.  This means my keyboard shortcuts for volume control (using amixer) don't always work since they don't always reference the correct device.

Is there any way to keep this from happening and keep the audio device assignments stable?  Video is on the motherboard and there is no way to disable HDMI in the system BIOS. I've tried blacklisting the snd_hda_codec_hdmi module but that has had no effect.

---

### Post by brainwash on 2012-07-17
Try to blacklist **snd_hda_intel** instead.

---

### Post by mastablasta on 2012-07-17
also try 
 
sudo alsa reload -c
 
when the sound is missing.

---

### Post by cbraxton on 2012-07-18
Thanks, I tried those things but it didn't work, the audio devices still change unpredictably when rebooting. It's probably part of a larger issue, I have two DVD burners and they keep switching /dev/sr0 and /dev/sr1, I never know ahead of time which drive is going to be 0 or 1.

What I've done for the moment is to add another set of hot keys to invoke "amixer -c 1" so if one set of volume control keys doesn't work the others can be used.

---

### Post by jmfal on 2012-07-19
Run this in a terminal and post output:

```
 aplay -l   
```

---

### Post by jmfal on 2012-07-19
I am trying to find file to edit to set your default card, but I cant find it right now.
It used to be acsound.conf
But the file name was changed
This might help for the  time being.
install pulse audio volume control:

```
 sudo apt-get install pavucontrol   
```

To set card you want as default  click on fallback

Hope that helps.

---

### Post by cbraxton on 2012-07-22
Actually, it looks like blacklisting the snd_hda_intel module did actually do the trick - I'd forgotten which key bindings I had configured to adjust sound card #0 vs. sound card #1 and was using the wrong ones for testing! (D'oh!) Now with that sorted out, I've rebooted quite a few times and it's working fine. The pavucontrol and aplay utilities both now show the sound blaster card as the only one in the system. Thanks!

(Now if I can only find a way for the two DVD drives to consistently come up with the same device nodes at each bootup...)

---

