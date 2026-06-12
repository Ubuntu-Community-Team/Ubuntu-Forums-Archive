---
title: "Need help | Wont let me enable show mouse in compizconfig"
date: 2011-04-03
forum: General Help
---

### Post by nsk tacticzz on 2011-04-03
hey guys im trying 2 get different cursor effects, and when i click show mouse in compiz config i can edit the settings, but it wont let me click the enable button, ill show some pics.

wont let me enable the thing in the photo, please help me

thanks

---

### Post by stinkeye on 2011-04-03
Check you have the plugin
ccsm > Utility > mouse position polling
enabled.

---

### Post by nsk tacticzz on 2011-04-03
> **stinkeye said:**
> Check you have the plugin
ccsm > Utility > mouse position polling
enabled.

how do i get to ccsm?

---

### Post by nsk tacticzz on 2011-04-03
> **stinkeye said:**
> Check you have the plugin
ccsm > Utility > mouse position polling
enabled.

mouse position polling inst in my utility, please help

---

### Post by stinkeye on 2011-04-03
May be in the package compiz-fusion-plugins-extra.
Search in the software centre
or 
in the terminal to install...
```
sudo apt-get install compiz-fusion-plugins-extra
```
May have to log out/in or restart compiz.


**[COLOR="Red"]Edit[/COLOR]** mouse polling appears to be in the package **compiz-fusion-plugins-main**
which is installed with compiz so not sure why you don't have the mouse polling plugin.

---

### Post by nsk tacticzz on 2011-04-03
> **stinkeye said:**
> May be in the package compiz-fusion-plugins-extra.
Search in the software centre
or 
in the terminal to install...
```
sudo apt-get install compiz-fusion-plugins-extra
```
May have to log out/in or restart compiz.


**[COLOR="Red"]Edit[/COLOR]** mouse polling appears to be in the package **compiz-fusion-plugins-main**
which is installed with compiz so not sure why you don't have the mouse polling plugin.

ok man, i downloaded some other stuff and it worked, how do i change the effect

---

### Post by stinkeye on 2011-04-03
Press super(Windows key) + k
and mess around with the options in **compizconfig-settings-manager** (ccsm)

---

