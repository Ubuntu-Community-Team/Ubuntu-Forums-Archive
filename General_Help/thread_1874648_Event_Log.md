---
title: "Event Log?"
date: 2011-11-03
forum: General Help
---

### Post by tommy2k10 on 2011-11-03
Is there an Ubuntu Event Log?  From time to time, my Ubuntu screen goes completely white and the only way I can get it 'fixed' is by turning the computer off!

---

### Post by Frogs Hair on 2011-11-03
Search for the log file viewer .

---

### Post by SparTacux on 2011-11-03
I'd be curious as to when it goes completely white

Are you normally using the computer when it happens or is it when you leave it for a while?

You can go through all the logs using log file viewer and check the exact time it happened with the log recording times. You may find something that corresponds to the time when it happens.

---

### Post by tommy2k10 on 2011-11-04
It happened yesterday when I left it for a while

---

### Post by SparTacux on 2011-11-04
It could be something to do with Power Management kicking in when the computer is left idle for a set amount of time - just an educated guess. Play around with Power Management settings for your monitor and set time for Display being put to sleep to say 5 minutes. Then wait 5 minutes and see what happens.

---

### Post by SteveDee on 2011-11-04
> **tommy2k10 said:**
> Is there an Ubuntu Event Log?

If your question is about Lubuntu (you posted your question in "Lubuntu") you might like to install a log viewer, as there is not one included in the basic Lubuntu install.

Open Synaptic, search for and install: gnome-system-log

---

### Post by claracc on 2011-11-04
You can find the log files in /var/log/, then I would see to dmesg, kern.log or Xorg.0.log in order to find the display error.

---

### Post by amjjawad on 2011-11-05
> **tommy2k10 said:**
> Is there an Ubuntu Event Log?  From time to time, my Ubuntu screen goes completely white and the only way I can get it 'fixed' is by turning the computer off!

And your OS is? release?
Your prefix says [[COLOR=Blue]**l**[/COLOR]ubuntu] while your post says [[COLOR=Sienna]**u**[/COLOR]butnu]!

---

