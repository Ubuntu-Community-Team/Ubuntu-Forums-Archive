---
title: "no snd-hda-intel after rmmod"
date: 2009-11-02
forum: General Help
---

### Post by DataMatrix on 2009-11-02
Hello, I've rmmod-ed snd-hda-intel from my freshly updated to 9.10 notebook in an attempt to install oss. After a while it turned out that I'm not happy with oss in 9.10 and tried to revert to alsa. The problem is that I can't modprobe snd-hda-intel back, it seems to be missing and is nowhere to be found. Can anybody help me restore it, I really need sound and reinstalling the entire OS is just not an option for me.
I know I may sound stupid, but I'm still inexpirienced and I tend to do stupid things :frown:

---

### Post by Giblet5 on 2009-11-02
The rmmod command doesn't physically remove the module. It just stops the kernel from using it (temporarily).

Post the output of ```
lsmod | grep snd
```

What happens when you run this command: ```
sudo modprobe snd-hda-intel
```

---

### Post by DataMatrix on 2009-11-02
lsmod | grep snd
is empty

sudo modprobe snd-hda-intel
I get something like "file not found"

---

### Post by Giblet5 on 2009-11-02
Did you physically remove the module at some point?

Did you remove the alsa-base package?

```
sudo apt-get install alsa-base alsa-utils alsa-tools-gui
```

Then try ```
sudo modprobe snd-hda-intel
```

Here is the [thread on the Intel sound chip]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

---

### Post by DataMatrix on 2009-11-03
I did not remove alsa-base and I've only added alsa-tools-gui after running your apt line
sudo modprobe snd-hda-intel
still did nothing so I whent to look around the HdaIntelSoundHowTo and at some point I found out about AlsaUpgrade which fixed the problem in about 1 minute.

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
```
sudo ./AlsaUpgrade-1.0.21-4.sh -r
```

---

