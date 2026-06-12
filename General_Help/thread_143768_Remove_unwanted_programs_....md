---
title: "Remove unwanted programs ..."
date: 2006-03-13
forum: General Help
---

### Post by wannabelinuxconvert on 2006-03-13
Hi,

Is there anyway I can remove unwanted programs manually !?

What I mean by this is I'd like to remove stuff like OpenOffice, Evolution, Bluetooth Utils and a whole host of other things that I'm never going to use.

When I choose to completely remove them through synaptic it always wants to uninstall parts of Gnome and something called Ubuntu-Desktop.

Now I have been through this before letting it uninstall everything it said it needed too and it completely wrecked my machine so had to do a clean install :confused: 

I have read in the forum that it's okay to remove Ubuntu-Desktop but it should always be re-installed as it manages the updates or something, but if I say remove Bluetooth Utils, and then okay it to uninstall Ubuntu-Desktop also, then re-install Ubuntu-Desktop it re-installs Bluetooth Utils :mad: 

So is there a clean, successful, non-system-damaging way to remove programs/daemons I have no use for and will never use, as I'm sure they're hogging hundreds of megabytes of space and memory !!

If there isn't then I think I've just found my first tick for Windows vs Ubuntu as Ubuntu has so far won hands down everything else I've thrown at the two, but Windows does let you un-install part's of the system you're never going to use but come packaged as standard without much of a fuss.

Any help will be greatly appreciated.

Mic

---

### Post by meborc on 2006-03-13
i always remove things by using synaptic... and check the items i don't want anymore to be removed completely... and if ubuntu-desktop uninstalls, it is no problem as it is only a meta-package... 

i have never heard that it is any way damaging NOT to have ubuntu-desktop... it is just silly...

it most certanly DOES NOT manage updates... for that you have a small program called update-manager (or smth) :D

i **sudo apt-get update && upgrade** every time i log on anyway... so it doesn't matter to me really...

---

### Post by Gustav on 2006-03-13
It's nothing wrong in removing ubuntu-desktop since it's just a meta-package that makes sure other packages are installed.

But if you dist-upgrade from an old version of Ubuntu to a new one (like Breezy->Dapper) you might want to install the package since it makes sure that new standard packages are installed. (For example in Hoary->Breeze (or was it Warty->Hoary?) it made sure that the update-notifier were installed)

---

### Post by meborc on 2006-03-13
yes... you have a point here... 

you see, ubuntu-desktop is a metapackage, allowing you to install all the nice packages forming the basic ubuntu easily, by just **sudo apt-get install ubuntu-desktop**... now if there is a distro change, some of the old packages are dropped and some new programs are created... since you don't know what they are or what they are named, it is logical to just use again the ubuntu-desktop packages to get them all... BUT it will install alot of things which you have already uninstalled... 

there is a workaround though... do **sudo apt-get install ubuntu-desktop** and you see all the names of the packages it tries to install... to the answer [Y/N] chose N and you are back in the commandline... now do manually **sudo apt-get install all the package names that you want** and you get those that you want installed and those that you don't need dropped...

oh i hope i made any sence :mrgreen:

---

### Post by Titus A Duxass on 2006-03-13
You could try approaching this from the over direction.

Do a minimal install i.e. server-expert and then add the packages that you want.

I had the same problems as you and found that this not only provided a satisfactory solution it also does a lot for your eduction.

---

### Post by wannabelinuxconvert on 2006-03-13
Hi,

Will try giving most things an uninstall this evening, it just worries me when I wants to remove something gnome related as I say last time this happened it ended up wrecking my desktop.

I did try the other route, and try a server install, and then tried XFCE4 but for some reason I couldn't get it to work with my monitor and tried several different configs before I gave it up as a bad job and returned to Gnome.

On the other hand, is there any way to do a server install, and then just install the most basic Gnome package !?

Thanks

Mic

---

### Post by meborc on 2006-03-13
you wrecked your desktop because you probably uninstalled way too many things... so uninstall only the things you KNOW what they are and you KNOW you will never need...

for simple setup try: [https://wiki.ubuntu.com/Installation/LowMemorySystems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

---

