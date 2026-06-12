---
title: "GTK+ theme engine errors in Appearance Preferences"
date: 2009-08-02
forum: General Help
---

### Post by DGeeez on 2009-08-02
It says the GTK+ theme engine for 'nimus' is not installed, but Synaptic says that I have:

nimbus-icon-theme
gtk-qt-engine
gtk2-engines

I can't find any more nimbus items in Synaptic (searching under ALL) than the one listed above, and other gtk items (there's a lot of them) all seem to be specified for something other than nimbus. What am I doing wrong?

Thanks.

---

### Post by ibutho on 2009-08-02
You only have the nimbus icon theme. If you want the gtk2 engine and theme, install gtk2-engines-nimbus.

---

### Post by DGeeez on 2009-08-03
> **ibutho said:**
> You only have the nimbus icon theme. If you want the gtk2 engine and theme, install gtk2-engines-nimbus.

You may not believe this, but first the message only specified GTK+, not GTK2 (oh, maybe the "+" is for anything subsequent?). I had already searched on "nimbus", which revealed one item only, the icon theme which I listed above. Just now, I punched the file you gave me precisely into Synaptic, which dumped way too much when I punched in the word GTK and nautilus, still does as gtk2-engines-nimbus. There's files just like this ending in -murine, -wonderland, and lots others, but not -nimbus! Is nimbus something a little too new which I stumbled on?

Anyway, I guess I'll see if apt-get can find this file, cause if it isn't at the top of this huge list and it's been typed correctly (checked it +twice), then maybe I know why some people hate Synaptic!

Update - apt-get couldn't find that file either, and with "nimbus"ware being all over the gnome-look site, I sure hope somebody understands what's going on with it. 

By the way, I checked my Software Sources, which have never caused me problems recently. 
Don't think I can really upload to this site the screenshots which I just took, and I don't have anywhere else to post them right now, but I do have the main, universe, restricted, and multiverse repos enabled, and under Third-Party-Software I have the archive-canonical, ppa.launchpad.net/awn-testing, as well as the Medibuntu repos. All except ppa.launchpad are for Jaunty, which I have installed (can't remember why I ever enabled ppa.launchpad, which specifies ubuntu-karmic at the end of it's name).

---

### Post by 4Orbs on 2009-08-03
The Nimbus engine and theme can be found [HERE]("http://www.gnome-look.org/content/show.php/Nimbus+(+Debian+and+Ubuntu+packages+)?content=70212"). If you double click the .deb file, it will install the engine and theme.

---

### Post by ibutho on 2009-08-03
> **DGeeez said:**
> You may not believe this, but first the message only specified GTK+, not GTK2 (oh, maybe the "+" is for anything subsequent?). I had already searched on "nimbus", which revealed one item only, the icon theme which I listed above. Just now, I punched the file you gave me precisely into Synaptic, which dumped way too much when I punched in the word GTK and nautilus, still does as gtk2-engines-nimbus. There's files just like this ending in -murine, -wonderland, and lots others, but not -nimbus! Is nimbus something a little too new which I stumbled on?

Anyway, I guess I'll see if apt-get can find this file, cause if it isn't at the top of this huge list and it's been typed correctly (checked it +twice), then maybe I know why some people hate Synaptic!

Update - apt-get couldn't find that file either, and with "nimbus"ware being all over the gnome-look site, I sure hope somebody understands what's going on with it. 

By the way, I checked my Software Sources, which have never caused me problems recently. 
Don't think I can really upload to this site the screenshots which I just took, and I don't have anywhere else to post them right now, but I do have the main, universe, restricted, and multiverse repos enabled, and under Third-Party-Software I have the archive-canonical, ppa.launchpad.net/awn-testing, as well as the Medibuntu repos. All except ppa.launchpad are for Jaunty, which I have installed (can't remember why I ever enabled ppa.launchpad, which specifies ubuntu-karmic at the end of it's name).

I am using Linux Mint and not regular Ubuntu. When I posted above I thought the package was available in the regular Ubuntu repos, but it seems like its only available in the Mint repos. Anyway try the suggestion in the post above and see how things go.

---

### Post by DGeeez on 2009-08-03
> **4Orbs said:**
> The Nimbus engine and theme can be found [HERE]("http://www.gnome-look.org/content/show.php/Nimbus+(+Debian+and+Ubuntu+packages+)?content=70212"). If you double click the .deb file, it will install the engine and theme.

Thanks!

---

