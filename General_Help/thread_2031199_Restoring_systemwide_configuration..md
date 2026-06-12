---
title: "Restoring systemwide configuration."
date: 2012-07-21
forum: General Help
---

### Post by emshains on 2012-07-21
Hello,
My motherboard recently gave away and now I will be replacing it with a different motherboard, different chipset and generation. I was running ubuntu 10.04 up until this point and had it set up just right, gnome was configured to act just the way I needed to be most productive with my multi-monitor setup. 
My question is this, is there a way to extract the list of packages from my boot drive and have the packages installed on a different install of 10.04 ? And could I get away with just copying /home/*  over to my new installation  ?

An unrelated question- is there any major distribution left that has stuck to gnome2 instead of gnome3 or any other "new" desktop environment ? I find gnome 3 to be great on a laptop, but it was cumbersome to use on a full size desktop.

Thank you for your help.

---

### Post by sudodus on 2012-07-21
> **emshains said:**
> Hello,
My motherboard recently gave away and now I will be replacing it with a different motherboard, different chipset and generation. I was running ubuntu 10.04 up until this point and had it set up just right, gnome was configured to act just the way I needed to be most productive with my multi-monitor setup. 
My question is this, is there a way to extract the list of packages from my boot drive and have the packages installed on a different install of 10.04 ? And could I get away with just copying /home/*  over to my new installation  ?

An unrelated question- is there any major distribution left that has stuck to gnome2 instead of gnome3 or any other "new" desktop environment ? I find gnome 3 to be great on a laptop, but it was cumbersome to use on a full size desktop.

Thank you for your help.

Yes there are ways to do that. One of them is to keep your /home directory on a separate partition :-)

Remember also that Ubuntu is much more portable than Windows. If you have not installed any proprietary drivers (typically for graphics and wifi), and if you are not starting programs which depend on particular hardware, it will run in another computer or with a new mobo, so just move or clone your harddrive and try it!

Yes, for example Linux Mint with Mate (a fork of gnome 2).

*Edit*: You might need to disable the proprietary driver(s) and replace with the built-in driver, and then later on install some new proprietary driver(s).

---

### Post by emshains on 2012-07-21
I have my /home on a different partition. 
The mistake I made was that I only left 10 gigs for the root partition and so I had to resort to making a /temp partition on a different drive, the same goes for swap. This did, however, make the system a bit faster. 
I will try to run it off of the default bootdrive then.

I know that Mate is a fork of gnome2, but doesn't it use mutter for rendering ? This is one of my main concerns about the new DE's as they use slow and uncustomizable window managers such as mutter. I prefer Compiz.

---

### Post by sudodus on 2012-07-21
The developers abandoned gnome 2, so I guess it will only be supported in already existing distros and versions, for example Ubuntu 10.04 LTS until April 2013.

If you are not happy with gnome 3, I suggest that you start testing other desktop environments. XFCE (as in Xubuntu) is a good alternative if you want something more fancy than LXDE. If your computer will get enough horsepower with the new mobo, you can also consider KDE. And don't forget that there are people who publish 'how-to tweak gnome 3' links.

But this is another topic than the title, and you might get better tips about it if you start a new thread dedicated to desktop environments.

---

