---
title: "Natty headphone output problems on Toshiba"
date: 2011-06-12
forum: General Help
---

### Post by matthewmke on 2011-06-12
Hello,

I'm a newbie, running Natty 11.04 on a Toshiba Satellite L645D laptop. If I boot the computer with headphones or an external speaker connection plugged into the headphone jack, I get no output through it. If I plug the headphones in after boot up, audio comes through fine, but there is no "auto-mute" on the internal speakers. If I restart/reboot after having had headphones plugged in, even if they are unplugged during the reboot, I again get no output through the headphone jack. I have to actually shut the computer down, then start back up in order to regain the headphone audio.
I've looked through previous threads discussing similar issues and tried updating, checking the ALSA settings (and I, like seemingly many other users, have no option to control headphone sensitivity, or whatever it was called). 
I don't have a lot of time to mess around trying to fix this, so I'm kind of wondering if I can just download another version in which this is not an issue? Maybe the stable release?
If anyone can give me some pointers it'd be greatly appreciated. Thanks in advance.

---

### Post by matthewmke on 2011-06-12
Well, I hope not to jinx myself by speaking too soon, but I seem to have fixed the problem after doing a bit more research. 

If anyone else is having issues with the audio output through the headphone jack on a Toshiba laptop in the Satellite series, this may be the fix for you:

Open terminal and type:


 **gksudo gedit /etc/modprobe.d/alsa-base.conf**

editor will open up, and at the end of the file add this line:

**options snd-hda-intel model=thinkpad position_fix=1 enable=yes**

Then save it, exit and reboot. 

I have seen slight variations on these lines, but this is the one that (so far) worked for me.

---

