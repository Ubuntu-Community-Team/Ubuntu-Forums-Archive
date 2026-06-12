---
title: "Nvidia driver messed me up bad"
date: 2010-01-28
forum: General Help
---

### Post by Silvertones on 2010-01-28
I thought I'd try the moderete effects under appearance. Got a message to update drivers. I did that. Rebooted and the desk top partially comes up but I can't do anything. Things are REAL slow and most of the graphics never show. On the desk top the stuff in the upper right corner is missing. If I go to file system it won't show the folders. I tried to turn off the effects the appearance screen comes up but clicking on the tab does nothing. How to I fix this. Can I back up and get rid of these drivers.

PLEASE help and be simple in the explanation.

---

### Post by overdrank on 2010-01-28
Hi and what version of Ubuntu are you using? Can you use the alt, F2 keys and enter the command ```
metacity --replace
```

---

### Post by Silvertones on 2010-01-28
Well I finally was able to get into prefs/appearance/visual effects and turn it off so I guess I'm OK. How do I now uninstall these Nvidia drivers?
I can now get into terminal. What will the above code do?
Karmic 9.1
And thanks

---

### Post by overdrank on 2010-01-28
> **Silvertones said:**
> Well I finally was able to get into prefs/appearance/visual effects and turn it off so I guess I'm OK. How do I now uninstall these Nvidia drivers?
I can now get into terminal. What will the above code do?
Karmic 9.1
And thanks

Hi and if you installed the drivers via system, administration, hardware drivers then you can just disable them. The command ```
metacity --replace
``` just turns compiz off. :)
What is the model of the nvidia graphics?
 You can use the command ```
lspci | grep VGA
``` to identify the hardware.

---

### Post by Silvertones on 2010-01-29
The drivers them selves seem to be fine. It was just enabling effects brought the computer to it's knees.
It's only a PIII 1.2 with 512 Ram & it's a lappy with shared vid mem.
As a side note how do I enter that vertical line that is in between lspci    grep VGA

---

### Post by Cheezespread on 2010-01-29
The pipe ( |) is the one above Enter/Return key in your keyboard with Shift pressed.

(Shift + \ )

---

### Post by Silvertones on 2010-01-29
Thanks for the pipe info-- |

The drivers are listed in synaptic package manager as:
1. Nvidia-96-Kernel-source
2. Nvidia settings

I should just be able to uninstall from there right?
It will then go back to the default drivers ?

---

