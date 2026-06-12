---
title: "Double Battery Icon"
date: 2011-10-27
forum: General Help
---

### Post by dmoconnell on 2011-10-27
I'm having a minor (major, if your OCD ;) ) problem. I'm running Ocelot with Unity. When I log into my primary account I get a double battery (see snapshot below) when i hover over the left one it says "Laptop battery is charged" but when i click on it, it does nothing. The right one does the opposite. (hovering does nothing but clicking brings up controls) When I log into the Root account It only shows 1 battery icon which tells me that it is only my account that is messed up. Does anyone know of anything I can do to reset the indicator apps bar (i think thats what its called) so that it only shows 1 battery icon
Thanks Dm

---

### Post by dmoconnell on 2011-10-31
Ok so i tried unistalling (using synaptic package manager doing a complete removal) indicator-power logged out and back in, still saw the extra battery icon. so i reinstalled indicator-power hoping that would (in any case) set it right. nope still seeing an extra battery icon in my primary account (in Ubuntu 3D, and not in Ubuntu 2D, Gnome (shell) or Gnome Classic) 
Any help would be greatly appreciated
Dm

---

### Post by christopher.wortman on 2011-10-31
Because you have Gnome shell installed, it re-enables the indicator icons. The new Unity uses it's own indicater thing called the "super menu" or some garbage. Basically Ubuntu being ignorant to already tested tried and true technologies and wanting to reinvent the wheel for no reason other than to be different.

---

### Post by dmoconnell on 2011-11-01
does anyone know how to remove the extra icon?

---

### Post by Frogs Hair on 2011-11-01
Try this because if you have searched you have probably not found any answers . Open the terminal and run the following .```
sudo apt-get remove indicator-power
``` 
Logout and back in open the terminal and reinstall the indicator .
```
sudo apt-get install indicator-power
```
Logout and back in or restart .

---

### Post by dmoconnell on 2011-11-02
Hi frogs, I tried what you said and the double battery still persists. any other ideas?
thanks 
Dm

---

### Post by Frogs Hair on 2011-11-02
I have looked for a command to reset the top panel in Gnome 3 , but can't find one . The command for Gnome 2 won't work . You could try unity --reset and it will reset the launcher , but I don't know about the top panel .

Try also , the purge command to remove the configuration files and reinstall.

Code : 

sudo apt-get purge indicator-power

---

### Post by dmoconnell on 2011-11-02
Hi again frogs. I tried the purge command and the unity --reset command and still nothing. Since I don't use Gnome-shell as much as I like I'm going to try the purge command on that (since christopher says its gnome-shell related) and see if that solves it.
Dm

---

### Post by dmoconnell on 2011-11-02
Hi again frogs. I tried the purge command and the unity --reset command and still nothing. Since I don't use Gnome-shell as much as I like I'm going to try the purge command on that (since christopher says its gnome-shell related) and see if that solves it.
Dm

to mods: Sorry for the double post, my computer decided to act up when i clicked submit

---

