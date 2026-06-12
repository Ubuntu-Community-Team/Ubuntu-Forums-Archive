---
title: "Controlling bluetooth control light"
date: 2010-12-17
forum: General Help
---

### Post by hernandez14 on 2010-12-17
Hi there,

I've just bought a MSI Wind U250 netbook and installed Ubuntu 10.10 64 bit. (Almost everything is working great out of the box. There are some little problems like dead keyboard shortcut Fn + F3 which sould be killing touchpad. BTW any package or other way to configure Fn keys?)

This model of netbook has a bluetooth as an option. My netbook hasn't BT, but has bluetooth control light anyway, which isn't used at all. Such a waste, I've paid for this control light after all... ;-)

I'm using GNUbiff as an e-mail notifier. It can run a command when a new e-mail comes. Now I'm using this to play a sound: play  /usr/share/sounds/purple/receive.wav. But **I would like to send this way a signal to the BT control light to light or, even better, start blinking in specified manner.** (Scroll Lock control light would be also great)

Is there such possibility? Maybe you are aware of existence of a package able to do this, because I'm unable to locate such one.

I think this is really obvious adaptation for control light and don't think I'm the first one who want such function. Some laptops even has a special control light just for e-mail (like my 12 years old fujitus-siemens) and there is Polish IM "EKG" (or "EKG2", don't remember) who blinks ScrLk when a new message comes, so I figured out there should be a potentiality to manage control lights... Am I right or wrong? Any ideas?

---

### Post by tredegar on 2010-12-17
**xset** can probably be used to do what you want.

Example:
```
xset led named "Scroll Lock"; sleep 1; xset -led named "Scroll Lock"
```
Makes my scroll lock led blink once.

See **man xset**

---

### Post by hernandez14 on 2010-12-17
Yes, indeed, xset can be used to do this, thank you!

I wrote a bash script named mail-led which is started when new message comes:
```
#!/bin/bash 

play /usr/share/sounds/purple/receive.wav 
while [ 1=1 ] 
do 
  xset led named "Scroll Lock"
  sleep $1
  xset -led named "Scroll Lock"
  sleep $2
  xset led named "Scroll Lock"
  sleep $2
  xset -led named "Scroll Lock"
  sleep $2
done
```and a second one mail-stop, executed when i double click gnubiff

```
#!/bin/bash

killall mail-led
xset -led named "Scroll Lock"
gnome-terminal --title="e-mail" -e "alpine -i"

```I suppose there are more elegant ways to do this (especially the infinite loop is retarded I guess ;) ) and if you can see any serious mistakes please let me know. I don't write even so simple scripts every day :)



But xset can only manage with ScrLk, CapsLk and NumLk LEDs, **not bluetooth led** as far as I've figured it out. ScrLk is good enough, but BT would be better, so if anyone know how to blink BT led I would be grateful.

---

