---
title: "Sound icon/Rhythmbox gone from panel?"
date: 2010-11-12
forum: General Help
---

### Post by s0dium on 2010-11-12
I have accidently removed the sound icon along with the rhythmbox controller from my panel. Could someone tell me how to get it back please?

---

### Post by ssulaco on 2010-11-12
Right click at top panel area,then left click (add to panel) scroll down to volume control,highlite it,click add button......
find rhythmbox ...applications -- sound/video -- rhythmbox...drag and drop to top panel

---

### Post by s0dium on 2010-11-12
Sorry in Meercat I don't see a Volume option. I am after the button for the panel that lets me stop and skip tracks etc.

---

### Post by plucky on 2010-11-12
> **s0dium said:**
> Sorry in Meercat I don't see a Volume option. I am after the button for the panel that lets me stop and skip tracks etc.

Right click on the panel and select "Add to Panel" and from the list that opens, select "Indicator Applet".

Good Luck

---

### Post by s0dium on 2010-11-12
Thanks I have tried that but adding an indicator does not make it re appear in meercat. What I am trying to add is a new feature only found in meercat.

---

### Post by Frogs Hair on 2010-11-12
You may have another problem because the indicator applet is what displays the sound icon / rythmbox in 10.10.

---

### Post by s0dium on 2010-11-12
I knew it did in the previous release but adding the volume slider does not add the rhythmbox controller in meercat : / I deleted it by accident and now am completely confuzzled on how to get it back.

---

### Post by Frogs Hair on 2010-11-12
System > Administration > Synaptic Package Manager , in the search box enter indicator-applet then right click on that line and mark for reinstallation and select apply by the green arrow. This may restore missing functions.

---

### Post by s0dium on 2010-11-13
Thanks I have since been able to restore it by doing this:

mkdir ~/.oldpanel
then
Code:
mv ~/.gconf/apps/panel ~/.oldpanel
then
Code:
gconftool-2 --shutdown
finally
Code:
pkill gnome-panel

Thanks for your help.

---

### Post by airstrike on 2011-05-19
> **s0dium said:**
> Thanks I have since been able to restore it by doing this:

mkdir ~/.oldpanel
then
Code:
mv ~/.gconf/apps/panel ~/.oldpanel
then
Code:
gconftool-2 --shutdown
finally
Code:
pkill gnome-panel

Thanks for your help.

^ This is what's wrong with Ubuntu/Linux.

---

### Post by rare HERO on 2011-06-23
> **plucky said:**
> Right click on the panel and select "Add to Panel" and from the list that opens, select "Indicator Applet".

Good Luck

That worked for me thanks.

---

