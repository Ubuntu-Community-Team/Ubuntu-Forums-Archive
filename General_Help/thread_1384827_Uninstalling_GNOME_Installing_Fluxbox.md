---
title: "Uninstalling GNOME Installing Fluxbox?"
date: 2010-01-18
forum: General Help
---

### Post by N9NE on 2010-01-18
Is that possible, I am trying to save some disk space and wouldnt want to have Gnome as well as another window manager installed on my system on the same time  ( other than xfce) 

How would i be able to delete all major components for gnome?

Thanks;

N9NE


(Karmic Koala)

---

### Post by SinxarKnights on 2010-01-19
> **N9NE said:**
> Is that possible, I am trying to save some disk space and wouldnt want to have Gnome as well as another window manager installed on my system on the same time  ( other than xfce) 

How would i be able to delete all major components for gnome?

Thanks;

N9NE


(Karmic Koala)

Hi. You don't have to remove Gnome to do this. you can just install fluxbox either by ```
sudo apt-get install fluxbox
``` or by the package manager.

then logout, and on the login screen select "Session" and change it to Fluxbox then login.

Trying to uninstall Gnome may remove much more than just the interface.

---

### Post by pmlxuser on 2010-01-19
I think the command to execute is 
```

$ sudo apt-get purge ubuntu-desktop

```

WARNING
The command might also remove other programs that are dependednt on gnome desktop so be sure of what you are doing

GOOD NEWS
with little skills in CLI you can get most of the programs to install againg after installing your prefered desktop manager as long as it compatible (which most of the time is)

---

### Post by HandyAndy on 2010-01-19
Rather trying to hack out Gnome, I think it would be easier and less time-consuming in the long run - and certainly safer - to back up your data and do a clean install of just what you want.

If you want a Ubuntu based system without Gnome but with xfce and fluxbox, it seems to me there are two obvious routes.

First, install Xubuntu and then install fluxbox.
Pro - you'll have a fully working system into which you can load your backed-up data and be up and running right away.
Con - if performance/space are serious restrictions, this may not save you enough of either, though it will certainly be smaller/lighter than Ubuntu + Gnome.

Second, you could do a minimal install and then build it up, adding only what you need/want, including xfce and fluxbox.
Pro - You'll have a tailor-made system no bigger or heavier than your needs require.
Con - It will take some time, effort, research and some knowledge of what you actually need to make up a fully functioning system.

Personally I'd go with the first and see if it meets your needs. If it doesn't, then you can have a go at the more hardcore option.

---

### Post by bodhi.zazen on 2010-01-19
> **HandyAndy said:**
> Rather trying to hack out Gnome, I think it would be easier and less time-consuming in the long run - and certainly safer - to back up your data and do a clean install of just what you want.

If you want a Ubuntu based system without Gnome but with xfce and fluxbox, it seems to me there are two obvious routes.

First, install Xubuntu and then install fluxbox.
Pro - you'll have a fully working system into which you can load your backed-up data and be up and running right away.
Con - if performance/space are serious restrictions, this may not save you enough of either, though it will certainly be smaller/lighter than Ubuntu + Gnome.

Second, you could do a minimal install and then build it up, adding only what you need/want, including xfce and fluxbox.
Pro - You'll have a tailor-made system no bigger or heavier than your needs require.
Con - It will take some time, effort, research and some knowledge of what you actually need to make up a fully functioning system.

Personally I'd go with the first and see if it meets your needs. If it doesn't, then you can have a go at the more hardcore option.

If you wish you can try Zenix. It is XFCE + Fluxbox + a few additional features.

It takes 1.5 Gb or so when installed and is fully compatible with Ubuntu : (when you install, skip the language packs, lol )

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

---

