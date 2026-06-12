---
title: "Changing/removing apps in Lubuntu"
date: 2010-07-02
forum: General Help
---

### Post by winecurmudgeon on 2010-07-02
I want to change or remove some of the standard apps in Lubuntu -- WICD for network manager, take off PyNeighborhood, and a couple of other things. But when I go to do it through synaptic, I'm told I also have to remove the Lubuntu desktop. Which, obviously, I don't want to do.

So, two questions: Is this just the metapackage, in which nothing will happen if it is removed? Or do I need make these changes through the command line?

I've been actually quite impressed with Lubuntu. It is working quite nicely on a 10- or 12-year-old Compaq Presario with 177 megs of memory and a Celeron process. The video lags a little, but the wireless, using a Netgear USB dongle, is terrific,

---

### Post by warfacegod on 2010-07-02
lubuntu-desktop is a metapackage. That means that all it does is make sure all desktop application packages get pulled in. It doesn't contain anything in and of itself and is safe to remove. The same holds true for all the 'buntu-desktop packages. The only other time you may need it is if you decide to do an Upgrade Install so reinstall it then. I almost never recommend that over a Fresh Install.

---

### Post by winecurmudgeon on 2010-07-02
Thanks. That will give me a project this weekend. And I learned my  lesson about clean installs vs. fresh installs when I installed Windows  98 over Windows 95. Whoops.

---

