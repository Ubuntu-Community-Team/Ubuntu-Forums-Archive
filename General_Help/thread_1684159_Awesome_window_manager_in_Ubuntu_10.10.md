---
title: "Awesome window manager in Ubuntu 10.10"
date: 2011-02-08
forum: General Help
---

### Post by patchwerkadams on 2011-02-08
I just installed the latest version of Awesome in Ubuntu 10.10 and I can't seem to get my configuration file to work in ~/.config/awesome/rc.lua

I copied it over from the /etc/xdg/awesome directory and if I edit the rc.lua file in that one I see changes in awesome. However, for some reason it doesn't detect any changes in my rc.lua located in .config/awesome/rc.lua. I double checked all of my permissions and everything looks good, is anyone else having this problem?

---

### Post by nosatalian on 2011-02-09
So I guess I'm not the only one...

---

### Post by Hawk__0 on 2011-03-30
And I guess I'm not the only one either.... and I'm on ubuntu 10.04

I did find something interesting.  If you man awesome, you will notice it looks for the config file (by default) in $XDG_CONFIG_HOME/awesome/rc.lua

now try to echo your XDG_CONFIG_HOME environment variable.  For me, it was blank.  Even after setting it and exporting it, and refreshing the config of awesome (super shift r by default?) it doesn't change a thing.

---

### Post by decomp on 2011-07-08
yeah sorry to drag up old stuff but ditto that. and uuuhh maybe this is a stupid question but what is all this $XDG business anyway? I can only find the freedesktop specifications which I do not find enlightening. Anyone have a link so I can learn whats going on?

---

