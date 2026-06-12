---
title: "Ubuntu is Slow with my Laptop"
date: 2009-12-18
forum: General Help
---

### Post by LeonLinux on 2009-12-18
[CENTER]Hello Ubuntu Folks!
The Performance of Ubuntu is slow with my laptop and it does not run smoothly
specs:
Cpu 2Gb Dual Core
Ram 2Gb
VRam 512Mb nVidia GeForce 8600M GT
I instaled nVidia the latest driver,
here is the picture when i move any window:
[IMG]http://www10.0zz0.com/2009/12/18/19/217038491.png[/IMG]
however, this is in Ubuntu 9.10 installed in Partition 20Gb Ext4, with Swap 4Gb
and Visual Effects in NORMAL, not EXTRA
Also i used Ubuntu 9.04 before,  same problem
any idea?
Thank you 

[/CENTER]

---

### Post by LeonLinux on 2009-12-19
[center][size=5]up[/size]

:(


[/center]

---

### Post by amsterdamharu on 2009-12-19
So you got the nvidia driver under system -> administration -> hardware drivers?
Looks like my windows installation with the default xp driver, after installing the driver it worked.

You can try to install compiz and run it to see if the driver is installed correctly. It should give you 3d effects.

---

### Post by Perturbed Penguin on 2009-12-19
This is likely not related at all but if you open up the configuration editor(gconf-editor) and navigate to apps/metacity/general see if the compositing_manager is checked... generally you do NOT want this checked. Again this shouldn't be related at all if you are truly using Compiz(desktop effects) but issues related to the Metacity compositing exhibit this kind of symptom.

Another idea is that perhaps you could vsync or un-vsync your Compiz effects, to do this open up CompizConfig(ccsm) and navigate to general options/display settings. Play around with the 'sync to vblank', 'detect refresh rate' and manual 'refresh rate' settings to see if any of those help at all - if you need you can reset these settings individually to their default settings using the button off to the right side of the window - if nothing in there helps then I recommend reseting these to their defaults.

Good luck, likely none of this will help but let's keep our fingers crossed! ;)

---

### Post by LeonLinux on 2009-12-19
> **amsterdamharu said:**
> So you got the nvidia driver under system -> administration -> hardware drivers?
Looks like my windows installation with the default xp driver, after installing the driver it worked.

You can try to install compiz and run it to see if the driver is installed correctly. It should give you 3d effects.

hello amsterdamharu
yes looks like windows xp used the default driver with slow performance,
 i used compiz before, it is also slow :(
then i formatted Ubuntu Partition and installed it again,  but didn't install compiz yet 

 about administration -> hardware drivers... and when i select nVidia driver to download ..it  will show me small window about downloading...but nothing download, it is keep at 0 progress.
any idea?
thank you

---

### Post by Perturbed Penguin on 2009-12-19
I think I have had that driver download issue myself, try quitting and reopening that hardware drivers window. On mine I also had to reboot before it actually showed that the driver had been installed and put into action. 

Btw, just in case you weren't aware, the 'normal' and 'extra' presets under the visual effects tab are actually just Compiz presets so if it let you check either of those it means it at least thinks you already have Compiz and therefore also already have your video drivers. Perhaps you don't have the video drivers installed and for some reason it still let you select one of those presets and this could be what is causing your issue? Anyways keep trying to get those drivers, I think you are on the right track. ;)

---

### Post by wojox on 2009-12-19
Try running:

```
sudo apt-get update && sudo apt-get upgrade
```

And check Jocky again.

That's some pretty serious tearing going on there. Your specs are great to. :confused:

---

### Post by LeonLinux on 2009-12-20
[LEFT]Hello everyone
i tried and did everything but nothing new :(
hope Ubuntu will fix this in the next version.
Thanks for your suggestions and help 

[/LEFT]

---

### Post by LeonLinux on 2010-01-12
Finally, solved the problem!! 

in nvidia-settings, i changed the resolution manually instead of auto, and Refresh Rate too

i did some changes with ccsm settings, in General-->General Settings-->Display Settings
then changed "Refresh Rate" to the same number of "Refresh rate" in nvidia-settings
enabled "Sync to vblank"
disabled "Detect refresh rate" and "Detect Output "

and then Reboot
done!

the problem was in Compiz, not nVidia or Ubuntu
now the performance is very very fast!
it is awesome, no more tearing
I'm happy now.
Thanks all :P

---

