---
title: "What dependencies do I need?"
date: 2011-05-31
forum: General Help
---

### Post by -gabe-noob- on 2011-05-31
Hey guys, I posed a thread in gaming/leisure about not being able to install savage 2 properly, but here's what I got in the terminal 
gabriel@gabriel-GA-MA790X-UD4P:~/Downloads$ ./Savage2Install-2.1.0.1-x86_64.bin

(<unknown>:7646): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed

(<unknown>:7646): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed
Segmentation fault
gabriel@gabriel-GA-MA790X-UD4P:~/Downloads$ 

From my limited knowledge those two GTk-critical lines are things that I need, and seeing as how I removed gnome-desktop in favor of kubuntu-desktop I was wondering theirs any packages that I need to make the seg fault stop happening

---

### Post by wildmanne39 on 2011-05-31
> **-gabe-noob- said:**
> Hey guys, I posed a thread in gaming/leisure about not being able to install savage 2 properly, but here's what I got in the terminal 
gabriel@gabriel-GA-MA790X-UD4P:~/Downloads$ ./Savage2Install-2.1.0.1-x86_64.bin

(<unknown>:7646): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed

(<unknown>:7646): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed
Segmentation fault
gabriel@gabriel-GA-MA790X-UD4P:~/Downloads$ 

From my limited knowledge those two GTk-critical lines are things that I need, and seeing as how I removed gnome-desktop in favor of kubuntu-desktop I was wondering theirs any packages that I need to make the seg fault stop happening
Hi, try this command in a terminal
```
apt-cache depends packagename
```

---

### Post by -gabe-noob- on 2011-06-01
will do when I get home. its not a package from synaptic so I didn't think that'd work sorry

---

### Post by Eruaran on 2011-06-15
I'm having the exact same problem with both Savage 2 and Heroes Of Newerth.

---

### Post by Eruaran on 2011-06-16
Well, I've managed to get Heroes Of Newerth working by typing:

unzip HoNClient-2.0.29.1.sh

This extracted everything to a folder called 'data' and from there I sould run the Hon.sh file and the game works mormally (yay).

I've extracted Savage2 in the same way and it creates a bunch of folders but I'm not sure what to do next with it as I can't see any sh file or anything... Not there yet but hopeful...

:popcorn:

---

### Post by lengau on 2011-07-30
Hi everyone,

I believe this bug is related to the oxygen-gtk theme in Kubuntu. Specifically, bug [278874]("https://bugs.kde.org/show_bug.cgi?id=278874") in KDE.

A workaround is to change your GTK theme. Installing the oxygen-molecule package gets you an Oxygen-lookalike theme for GTK apps that may work for you. I used that theme to install the apps and then switched back to oxygen-gtk.

If anyone has this issue with any programs not listed below, please add it to that KDE bugzilla post or (if you don't have a KDE bugzilla account) here and I will add it to the KDE bug.

Programs known to have this error:
Aquaria installer
Braid installer
Cogs installer
Cortex Command installer
Crossover installer
Hammerfight installer
Heroes of Newerth installer


Thanks a lot!

---

