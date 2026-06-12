---
title: "Audio output will not output sound to speakers"
date: 2011-07-19
forum: General Help
---

### Post by kgonepostl on 2011-07-19
Hey, I don't know anything about ubuntu. Could you guys help me out. I'm pretty knowledgeable with windows if you guys need a printout of something let me know. My friends getting really frustrated about this. Help!!i

So here's the situation. He plugs his audio jack into his computer and then into the speakers but it still plays from the computer speakers.

---

### Post by CatKiller on 2011-07-19
If you're using 11.04 then you just click on the volume icon, select Sound Preferences, go to the Output tab and change the Connector from the drop-down list for your output device. Can't remember how to do it on earlier versions.

---

### Post by kgonepostl on 2011-07-19
Ya he's on 11.4 but that didn't work. There's no other output options. There's only one. Stereo analog output or something very close to that and that output device isn't pumping out sound.

Update: After unplugging and plugging it back in it stopped working. This is screwy

---

### Post by kgonepostl on 2011-07-19
****bump
Also I don't remember if I mentioned this but there's only one sound output I can choose and it aint working correctly for the output. If you need me to take a screenshot I can do that too. Anything to help.

---

### Post by CatKiller on 2011-07-20
Some information on what you're using and how you've got it connected would help.

---

### Post by kgonepostl on 2011-07-20
3.5mm jack into the appropriate slot. Upgraded fully to 11.04. All upgrades are done. It's a laptop. I can't think of anything else that you would need. I don't know how to find out what chipset for his audio he has. Maybe that would help but I don't know linux.

---

### Post by eltonw on 2011-07-20
> **kgonepostl said:**
> 3.5mm jack into the appropriate slot. Upgraded fully to 11.04. All upgrades are done. It's a laptop. I can't think of anything else that you would need. I don't know how to find out what chipset for his audio he has. Maybe that would help but I don't know linux.

Are you sure that it isn't plugged into the ***microphone*** slot by mistake?

---

### Post by CatKiller on 2011-07-20
> **kgonepostl said:**
> It's a laptop.

OK, that's probably the critical bit. Have you checked to see if there's another device in the Hardware tab?

Otherwise, it appears to be a case of giving ALSA more information about the sound device so that it can detect the outputs properly. The laptop model number may be sufficient, or you may need to find out a bit about the sound devices; ```
sudo lshw -c multimedia
``` should do it.

Assuming a bunch of things, you might get away with adding

```
options snd-hda-intel model=laptop position_fix=1
``` to the end of your /etc/modprobe.d/alsa-base.conf

Otherwise, I managed to find a couple of links that might point you in the right direction.

[http://ubuntuforums.org/showthread.php?t=1488468](http://ubuntuforums.org/showthread.php?t=1488468)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ubuntu-headphone-599930/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/ubuntu-headphone-599930/)

---

