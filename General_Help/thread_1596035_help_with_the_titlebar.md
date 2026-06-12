---
title: "help with the titlebar"
date: 2010-10-13
forum: General Help
---

### Post by hotshot247 on 2010-10-13
i am using ubuntu 10.10 and i'm having a problem with my titlebar. the minimize, maximize, and close buttons aren't even on there at all like when i open nautilus to browse for files, the buttons are not there and when i go to certain things like i went to check my history in firefox, it didn't even have a titlebar at all and sometimes firefox doesn't have one at all either. does anybody know a way i can fix this? thanks!

---

### Post by steve-o1983 on 2010-10-13
> **hotshot247 said:**
> i am using ubuntu 10.10 and i'm having a problem with my titlebar. the minimize, maximize, and close buttons aren't even on there at all like when i open nautilus to browse for files, the buttons are not there and when i go to certain things like i went to check my history in firefox, it didn't even have a titlebar at all and sometimes firefox doesn't have one at all either. does anybody know a way i can fix this? thanks!

I am having a similar issue, the title bar has seemed to have disappeared (no maximize, minimize or close buttons).  I stumbled into this problem after I had logged out of the Desktop Edition into the Netbook Edition, when I logged back into the Desktop Edition is when I noticed that the title bar had gone missing.  Any help would be appreciated.

---

### Post by hotshot247 on 2010-10-13
now for some reason, i can't enable my desktop effects. i tried uninstalling and reinstalling my video driver with no luck. i wonder if it's some kind of bug with ubuntu 10.10? maybe their is a way around it.

---

### Post by hotshot247 on 2010-10-14
i just want to let ya know that i fixed it. it is a bug in compiz. what i did is go to synaptic package manager and type compiz and do a complete uninstall of everything that has to do with compiz. then when it's done, close synaptic and go to the terminal and type: 

sudo apt-get install compiz compiz-plugins compiz-gnome  compiz-core emerald compiz-fusion-plugins-main  compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager

and then it fixes it. let me know if you need anymore help.

---

