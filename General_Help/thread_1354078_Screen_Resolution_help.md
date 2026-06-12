---
title: "Screen Resolution help"
date: 2009-12-13
forum: General Help
---

### Post by D4Y.V on 2009-12-13
I'm new to the world of Ubuntu, and I was wondering, why doesn't my screen resolution go up to the normal amount it would in [my old operating software] Vista?
The Computer>Preferences>Display only goes to 800x600...
Can I have some help? and make it detailed, I'm not very lucky with computers, and I've only had Ubuntu for about 7 hours, most of which time was occupied by the Chess Simulator, and googling around for an answer to my question...
I have a Dell Dimension C521 with an Ndivia Graphic's card... the Screen has a maximum resolution of something like "somtingx2014 at 60Hz".
Think you for the advice/answers I would receive.

---

### Post by rafalcieslak on 2009-12-13
You won't be able to use high resolution until you install drivers for your Nvidia. System->Administration->Drivers (or something similar, as I have translated menus;P )

---

### Post by D4Y.V on 2009-12-13
I've installed the recommended drivers, I'm stuck on what to do next, because then I try to click on the Display setting is says "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" and id I say yes, there is no way to change Resolution size in the options under it.
In case there is and I'm misunderstanding something I'll list the options.
It comes up with a prompt box sprouting with jargon saying:
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
to which I click OK to.
"Nvidia settings configuration
[\] Enable ToolTips
[\] Display Status Bar
[\] Slider text entries
[ ] include X display names on the Config file
[\] Show "Really Quit?" Dialog
 [Save Current Configuration]
[Help] [Quit]"

It's a set of tick boxes and a save setting with help and quit buttons.

Hope that was enough info! Thanks again!

---

### Post by wojox on 2009-12-13
Did you reboot?

Run:

```
sudo nvidia-xconfig
```

From the terminal and then 

```
gksudo nvidia-settings
```

Configure everything and save.

---

### Post by D4Y.V on 2009-12-13
I just rebooted, Screen looks pimpin' I can't thank you 2 enough.
Is there a reputation system on this website?

---

