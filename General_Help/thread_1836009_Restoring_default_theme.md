---
title: "Restoring default theme"
date: 2011-08-30
forum: General Help
---

### Post by Tornikee on 2011-08-30
Hello, a couple of days ago I deleted all the themes - including the default one - in 11.04 in an attempt to clean their list up. Now I have one of the custom themes installed and have no problems with it, although the log in screen has become a very generic classic-style, guess because there's no specific theme the system can skin it in at the startup. 

Is it possible to restore/download the original default theme?

---

### Post by Frogs Hair on 2011-08-30
The Ambiance and Radiance themes are named light themes .```
sudo apt-get install light-themes
```

---

### Post by Tornikee on 2011-08-30
> **Frogs Hair said:**
> The Ambiance and Radiance themes are named light themes .```
sudo apt-get install light-themes
```
Thanks for the reply. I entered that command, and got this:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
light-themes is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded."

Although the themes are still not present in the Appearance window, nor in the "~/themes" folder. This probably is due to me playing around with themes that I mentioned in my post : /

---

### Post by thefasterblueone on 2011-08-30
Use 'Synaptic Package Manager' and search for 'themes'.

---

### Post by Tornikee on 2011-08-30
> **thefasterblueone said:**
> Use 'Synaptic Package Manager' and search for 'themes'.
Cheers for that, themes restored.

---

