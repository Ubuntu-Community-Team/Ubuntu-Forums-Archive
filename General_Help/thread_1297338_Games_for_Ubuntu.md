---
title: "Games for Ubuntu"
date: 2009-10-21
forum: General Help
---

### Post by Son of MaxVK on 2009-10-21
I am looking for help to install Counter Strike: Source and JKA (Star Wars Jedi Knight Jedi Academy) onto Ubuntu.

I saw somewhere else that it is compatible when using Wine, I just don't know how to set it up at all. My CS:S is part of steam and will need to download onto my system and JKA is on a CD.

Please be awear that I really don't know what I am doing so any advice needs to be basic or easy to understand xD sorry about that.

Thanks-

---

### Post by xxterry1xx on 2009-10-21
> **Son of MaxVK said:**
> I am looking for help to install Counter Strike: Source and JKA (Star Wars Jedi Knight Jedi Academy) onto Ubuntu.

I saw somewhere else that it is compatible when using Wine, I just don't know how to set it up at all. My CS:S is part of steam and will need to download onto my system and JKA is on a CD.

Please be awear that I really don't know what I am doing so any advice needs to be basic or easy to understand xD sorry about that.

Thanks-well if you have the latest wine 1.1.31 it would be better lol
anyways just download steam if you already haven't all you have to do is install wine hq 1.1.31
do these steps in order in terminal with
sudo -s
[I]
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[/I][I]
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list[/I]

[B]sudo apt-get  update
[/B][B]
sudo apt-get  install wine[/B][B]

type exit and exit again(this will exit the root and exit the terminal)

then download steam [http://store.steampowered.com/about/](http://store.steampowered.com/about/)
double click on SteamInstall.msi it should probably be on the desktop and it will install and all you have to do is login and download css and i never installed JKA on ubuntu before only on windows but if its 2 cds i recommend to put the files from both of the cds in the a folder(same folder goes for both) and run setup.exe or w.e the installer is and it should install and to launch the programs it would be in applications>wine

also if your going to game i suggest to install LXDE or XFCE and use that as your gaming desktop (reason why im saying this is because there more lightweight on memory and less cpu usage stuff like that)

so if you want to add those go to synapatic package manager and search LXDE or XFCE 
and when you log on go to options and go to select session you will find LXDE or XFCE and if you want to get back to gnome or KDE then select "gnome" or "KDE"
[/B]

---

### Post by Son of MaxVK on 2009-10-21
> **xxterry1xx said:**
> well if you have the latest wine 1.1.31 it would be better lol
anyways just download steam if you already haven't all you have to do is install wine hq 1.1.31
do these steps in order in terminal with
sudo -s
[I]
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
[/I][I]
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list[/I]

[B]sudo apt-get  update
[/B][B]
sudo apt-get  install wine[/B][B]

type exit and exit again(this will exit the root and exit the terminal)

then download steam [http://store.steampowered.com/about/](http://store.steampowered.com/about/)
double click on SteamInstall.msi it should probably be on the desktop and it will install and all you have to do is login and download css and i never installed JKA on ubuntu before only on windows but if its 2 cds i recommend to put the files from both of the cds in the a folder(same folder goes for both) and run setup.exe or w.e the installer is and it should install and to launch the programs it would be in applications>wine

also if your going to game i suggest to install LXDE or XFCE and use that as your gaming desktop (reason why im saying this is because there more lightweight on memory and less cpu usage stuff like that)

so if you want to add those go to synapatic package manager and search LXDE or XFCE 
and when you log on go to options and go to select session you will find LXDE or XFCE and if you want to get back to gnome or KDE then select "gnome" or "KDE"
[/B]

Ok, does it mean I simply install CS:S via the steam client (already installed) and will not need to do anything else?

---

### Post by earthpigg on 2009-10-21
> **xxterry1xx said:**
> 
also if your going to game i suggest to install LXDE or XFCE and use that as your gaming desktop (reason why im saying this is because there more lightweight on memory and less cpu usage stuff like that)

so if you want to add those go to synapatic package manager and search LXDE or XFCE 
and when you log on go to options and go to select session you will find LXDE or XFCE and if you want to get back to gnome or KDE then select "gnome" or "KDE"
[/B]

GNOME or KDE are both also fine for gaming, you just want to avoid the ubuntu-desktop metapackage.

the standard ubuntu desktop is fine for video games too, just like Vista...

and, as many think XP is better than Vista for gaming, many (myself included) also think standard ubuntu desktop is less than ideal.

do a command line install of ubuntu.

install your desktop environment of choice -- but nothing involving *buntu-desktop. 

if you want xfce, install xfce and not xubuntu-desktop.

if you want gnome, install gnome but not ubuntu-desktop.

et cetera.

or, if you have a powerful computer and dont care about having 80 frames per second instead of 65, you can just use normal ubuntu and be fine.

---

### Post by xxterry1xx on 2009-10-21
> **Son of MaxVK said:**
> Ok, does it mean I simply install CS:S via the steam client (already installed) and will not need to do anything else? no you just go to my games and right click on css and click play and it should work if there's any errors then copy and paste here or report to the wine hq devolopers

---

### Post by xxterry1xx on 2009-10-21
> **earthpigg said:**
> GNOME or KDE are both also fine for gaming, you just want to avoid the ubuntu-desktop metapackage.

the standard ubuntu desktop is fine for video games too, just like Vista...

and, as many think XP is better than Vista for gaming, many (myself included) also think standard ubuntu desktop is less than ideal.

do a command line install of ubuntu.

install your desktop environment of choice -- but nothing involving *buntu-desktop. 

if you want xfce, install xfce and not xubuntu-desktop.

if you want gnome, install gnome but not ubuntu-desktop.

et cetera.

or, if you have a powerful computer and dont care about having 80 frames per second instead of 65, you can just use normal ubuntu and be fine. yes i agree with that gnome,kde,LXDE and XFCE are good for gaming but i recommend a desktop that will focus more towards to less cpu usage and less memory and will be great for gaming i aint saying any desktop sucks i think there all great

o btw how to install those? without getting the Xubuntu-desktop or Ubuntu-desktop? (i have gnome and LXDE i just want to add KDE and XFCE to my collection lol)

wait is XFCE in synaptic XFCE4? Meta-package for the Xfce Lightweight Desktop Environment?

---

### Post by earthpigg on 2009-10-21
yes, just search synaptic and take a look at the results.

xfce4 is indeed the recent stable release of xfce.

i think kde is 4.3?

---

### Post by superdav42 on 2009-10-21
If you are still having problems look in the appdb:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=373]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731")
and here for jka:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315")

---

### Post by Son of MaxVK on 2009-10-22
I have installed JKA successfully but now when I start the game my moniter goes blank but everything is still running. I can hear the games menus ect, I use alt+sysrq+k to drop out and the monitor goes back to normal.

Do I need to update wine or somthing? I have 1.0.1.

---

