---
title: "Ubuntu Netbook Remix Desktop Switcher"
date: 2009-11-23
forum: General Help
---

### Post by i_baked_cookies on 2009-11-23
I just bought a nice little cheap netbook on sale, and I've wiped the crap Windows XP off of it, and now I'm running UNR 9.10.  It's delicious.  Anyways, I don't think I really like the default desktop interface that comes with UNR, I'd rather have a traditional Ubuntu desktop.  I do like the other UNR specific features though, so I don't want to go with a normal install of Ubuntu.

The Desktop Switcher app in the ap-get isn't available for some reason... how can I easily switch back and forth between the UNR desktop and the traditional desktop?

Thanks in advance.

---

### Post by blazemore on 2009-11-23
In order to install the package, make sure the [Ubuntu Netbook Remix repositories are in your repository list]("http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html"), and then install desktop-switcher either using apt-get or the Synaptic package manager.

---

### Post by snowpine on 2009-11-23
The Desktop Switcher was dropped from 9.10 because it was extremely buggy (unfortunately).

Please don't follow blazemore's instructions unless you are using 8.04 or 8.10.

---

### Post by i_baked_cookies on 2009-11-23
> **snowpine said:**
> The Desktop Switcher was dropped from 9.10 because it was extremely buggy (unfortunately).

Please don't follow blazemore's instructions unless you are using 8.04 or 8.10.

Ah, okay... so there's nothing I can really do except wait for something better to come out, or to install normal Ubuntu?

---

### Post by i_baked_cookies on 2009-11-26
Up for more ^

Are there any viable options to have a normal desktop with UNR?

---

### Post by tguh on 2009-12-20
> **i_baked_cookies said:**
> Up for more ^

Are there any viable options to have a normal desktop with UNR?

been searching the web for any option for 9.10. I just know that they drop it from 9.10 because it was buggy

---

### Post by ubun_two on 2009-12-20
All you have to do is to go to System->Perference->Session and uncheck netbook-launcher and maximus, so they would not run at start up.  Then add appropriate controls to your panel (like main menu).  When you restart your netbook, it should look and act like more traditional Ubuntu.

---

