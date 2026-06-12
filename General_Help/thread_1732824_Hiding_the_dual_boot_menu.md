---
title: "Hiding the dual boot menu"
date: 2011-04-18
forum: General Help
---

### Post by gesaugen on 2011-04-18
hi ppl
I have dual boot PC with XP and U10.10. Is it possible to set up dual OS boot menu that it is hidden in a way that i can still choose to boot which OS i want from that hidden menu.
Or even better, is it possible to set up automatic boot into XP in a way that boot menu isn't shown at all but that I can call boot menu via keystroke (like you call boot menu to go into the safe mode in XP options by pressing F8)?

---

### Post by oldfred on 2011-04-18
I have not used it but I see it recommended a lot:

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Slightly older gui to edit some things:
Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

All the details to manually do it:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by lithopsian on 2011-04-18
Sounds a bit complicated to me!  Especially for something that Grub already does.  You can hide the Grub menu completely and then make it appear by pressing Esc (it is Esc, right?).  You can also change the timeout before it just boots into the default OS.  Would that work for you?

---

### Post by gesaugen on 2011-04-19
oldfred and lithopsian, thanks for reply!

lithopsian, if I can hide Grub menu and call it via esc key, that would be great! 
So, does the esc key call the hidden grub menu?

---

