---
title: "Can't remove Docky anchor icon"
date: 2010-08-28
forum: General Help
---

### Post by benerickson1 on 2010-08-28
Hi, I would like to remove the anchor icon from Docky.  I found instructions to go into gconf-editor and set "apps/docky-2/docky/items/DockyItem/ShowDockyItem" to false.  Only problem is, this item does not appear.

The only folders in apps/docky-2/docky/items/ are ColoredIconDockItem and WnckDockItem.  Inside ColoredIconDockItem, there's a key called DockyItem set at value 193.  I tried changing/deleting that and restarting Docky, but it keeps defaulting back.  I also removed and reinstalled Docky, but I found the same thing.  Does anyone know how I can find the right value to change?  Thanks!

-Ben

---

### Post by M4he on 2010-08-28
It doesn't work with the Docky version from the official Ubuntu repos. However you could try installing the latest version from the Docky ppa, however I don't know if it will work with that version.

---

### Post by benerickson1 on 2010-08-28
I got the app from the Docky "stable" PPA and it was the same version as the Ubuntu repo.  Then I got the newest version from the "development" PPA and that one worked like I was hoping.  Thanks for the tip.

---

### Post by monkeyonapig on 2010-12-22
I've installed the latest docky, but I still can't get the icon to go away.

There is a "ShowDockyItem" option in configuration editor, but toggling it has no effect on my docky toolbar. When quit and restart docky, the icon is still there. Any ideas?

---

### Post by monkeyonapig on 2010-12-22
Nevermind!

Reinstalling Docky fixed everything!

---

### Post by Mc-G-non on 2011-02-16
There two official Docky PPAs. One with our bleeding edge version  built from Docky trunk and one including the latest build of the current  Docky stable branch. 
**The Docky Stable PPA** is [https://launchpad.net/~docky-core/+archive/stable]("https://launchpad.net/%7Edocky-core/+archive/stable") .  Use this PPA for the current, stable version of Docky. 
To use the Docky Stable PPA, for Ubuntu 10.04 (Lucid Lynx) **and later**: 
 [LEFT]  sudo add-apt-repository ppa:docky-core/stable
  sudo apt-get update
  sudo apt-get install docky
[/LEFT]
 **The Docky Development PPA** is [https://launchpad.net/~docky-core/+archive/ppa]("https://launchpad.net/%7Edocky-core/+archive/ppa") and typically lags behind the source by about a day.  Use this PPA for the most current, updated version of Docky. 
To use the Docky Development PPA, for Ubuntu 9.10 (Karmic Koala) **and later**: 
 [LEFT]  sudo add-apt-repository ppa:docky-core/ppa
  sudo apt-get update
  sudo apt-get install docky
[/LEFT]
 To update Docky, if you installed Docky as a package from either the official repositories or one of our PPAs, run: 
 [LEFT]  sudo apt-get update
  sudo apt-get upgrade
[/LEFT]

---

