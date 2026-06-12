---
title: "Strange menu bar on the desktop"
date: 2012-02-23
forum: General Help
---

### Post by viperdvman on 2012-02-23
On my netbook... I've discovered that I had some strange menu bar that's been popping up behind my Unity panel, visible only when it's semi-transparent like I have it set up. I didn't first notice it until I switched my theme to Radiance.

However, I didn't actually discover what it was until I installed and ran the Cinnamon desktop environment. What I discovered was the screenshot I've attached. A full menu bar to what looks like Nautilus. I killed Nautilus, and the menu bar goes away. However, when I start Nautilus back up, the menu bar comes back.

How do I get rid of it and keep it from popping back up like this (like it's not supposed to)? It's supposed to be in Unity's global menu, not popping up behind the Unity panel or showing up in Cinnamon.

---

### Post by IWantFroyo on 2012-02-23
Try running gconf-editor, and go to Apps->Nautilus->Preferences and unchecking show_desktop.
You may have to install gconf-editor, though. I can't remember whether they cut it out of Oneiric or not.

---

### Post by Frogs Hair on 2012-02-23
This is a bug and it is nautilus related .  A Unity 3D work around is to open the CCSM and Unity plug-in and slide  the opacity setting for the panel back and forth . The other method is open advanced settings >  desktop and turn off " have file manager handle the desktop." The problem with the last work around is that this will need to be turned on every time you want to drag a file on the desktop or use the context menu .

---

### Post by viperdvman on 2012-02-23
I have gconf-editor... but "show desktop" does not show under apps>nautilus>preferences.

I have done the CCSM work around... I actually found that to work, but it sucks that I have to do that every time I log into Unity. In Cinnamon, however, it gets to be a real pain, since the only way to remove it is from the Cinnamon Control Panel... and find "Let file manager handle the desktop". I did do that, and it killed my Unity. I had to do a unity --reset to get it back, but Unity is running again. I'm nervous to try it out in Unity... especially since it kills my context menus which I do use.

Any way I could keep it from happening in Cinammon, other than move my panel to the top. 'Cause if I remove that panel in Cinnamon, it breaks my Unity for some reason.

---

### Post by viperdvman on 2012-02-24
I actually found this to work. It was a widely-reported bug on Launchpad, and was patched appropriately. We just have to keep our eyes on this bug every time Nautilus is updated, as this patch doesn't seem to go upstream very well. [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771) (more specifically, comment #48 [link here]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771/comments/48"))

```
sudo add-apt-repository -y ppa:matttbe/ppa
sudo apt-get update
sudo apt-get install nautilus nautilus-data libnautilus-extension1 gir1.2-nautilus-3.0
sudo add-apt-repository -r ppa:matttbe/ppa
```This does correct the problem when running GNOME Shell or Cinnamon, but not when running Unity or Unity 2D. I still have to go into Ubuntu Tweak and slide the bar all the way to 100% and back to wherever I want it. (note... it works better in Ubuntu Tweak, as part of the Compiz window shows under the top panel on my netbook, and the transparency sort of engrains that inside... it seems more like a bug in the unity panel)

But it works. It killed the Nautilus menu bar on the desktop whenever I run Cinnamon on my netbook. So off to playing around with it :)

Even better, I hear that Precise won't have this problem :) If true, then I'm upgrading to Precise once it's stable.

---

### Post by neycho on 2012-02-25
[@viperdvman  ]("http://ubuntuforums.org/member.php?u=1367167")
That solution actually works for me  - Linux Mint 12 / Cinnamon 1.3.1, kernel 3.0.0.16 :) 
Thanks a lot! :)
[]("http://ubuntuforums.org/member.php?u=1367167")

---

