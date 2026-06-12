---
title: "compiz.real causes 100% CPU?"
date: 2010-02-01
forum: General Help
---

### Post by lasershadow on 2010-02-01
Hey,

So I'm running Karmic on AMD64x2, and I have Compiz. I have been running fine, but when I run top, I see that compiz.real always takes up 100% of one of the cores of my CPU. this happens even when I change the visual effects to none in the appearance preferences. This problem starts as soon as I log in. My graphics card is an nvidia 8400gs, which is not that good, and I've installed my drivers using envy. Does anyone have any ideas about this problem?

thanks.

---

### Post by geodanny on 2010-02-09
I recommend installing the package "compiz" in Synaptic Package Manager. It is a GUI manager for Compiz. You'll then find CompizConfig Settings Manager under System > Preferences. 

I had a very similar problem today. I opened the gui manager, unchecked the box for "Widget Layer" and voila, the CPU went down immediately. I take it compiz was looking for a widget program I likely do not have installed. Your problem may be something different, but I would uncheck a box at a time until you find out what the culprit might be.

---

### Post by Richard1979 on 2010-02-09
Are you using the Proprietary driver?
System > Administration > Hardware Drivers

Sounds to me like it's using the CPU because you don't have proper 3D drivers installed.

---

### Post by geodanny on 2010-02-10
Richard, I personally don't have proprietary drivers installed. I have a Dell Latitude D620 with an Intel graphics card. I am relying on whatever drivers Ubuntu chose to install. :-)

---

### Post by Richard1979 on 2010-02-10
> **geodanny said:**
> Richard, I personally don't have proprietary drivers installed. I have a Dell Latitude D620 with an Intel graphics card. I am relying on whatever drivers Ubuntu chose to install. :-)

The open source drivers don't support proper 3D though as yet.
For the OP, I'd just disable Compiz and use Basic mode if it's causing him/her problems.

---

