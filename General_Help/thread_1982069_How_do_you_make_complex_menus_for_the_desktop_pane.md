---
title: "How do you make complex menus for the desktop panels?"
date: 2012-05-17
forum: General Help
---

### Post by Manmadegod on 2012-05-17
Please don't get me wrong - I absolutely love the XFCE shell, which is perfectly sweet on my hardware - GNOME always had issues, which were just minor enough to be tolerated, although not quite happily.  I like it even more that it uses the same sane graphical toolkit as GNOME (this I really liked about GNOME), so that I almost don't miss the GNOME 2 interface. Well, almost, as I am a GNOME 3 refugee  - that is, a dissident who really couldn't stand its new,  stupendously useless, and weirdly religion-inspired Unity shell. I just had to get away from that evil regime , which has taken over the GNU shop and killed the benevolent goat while it's high priests were (likely) getting permanently stoned . I have already tried GNOME 2 alternative shells which are launched from GNOME 3 distros such as Linux Mint, but the only one with real GNOME 2 functionality got into a fight to the death with my hardware. As I just could not allow this to continue, I found my way to here, in relative peace, with Xubuntu Xfce.

The one thing that I miss enough to try and build again myself (if the point-and-click tools will facilitate this) is that triple-tab launcher on the GNOME 2 panel ,  **Applications| Places| System**.  Each tab in turn launches a branching menu which covered all applications, places, and system (system and preference) controls. Has anyone ever done this,  or just know if it's possible to build any kind of complex menu launchers (menus which branch in more than one dimension, and if possible are updated by the system when it changes).  I would be especially happy if this can be done with the Xubuntu GUI (someone probably has a nice, lengthy script for this somewhere, but I really don't have the developer skill to meld it with my system).  

Thanks.

---

### Post by rai4shu2 on 2012-05-17
You can actually have more than one Application Menu on a panel. Then just use custom menus for the ones you want with non-standard menus. I don't know how easy it is to do, but it can't be altogether hard.

see: [http://standards.freedesktop.org/menu-spec/1.0/](http://standards.freedesktop.org/menu-spec/1.0/)

---

### Post by Manmadegod on 2012-05-18
> **rai4shu2 said:**
> You can actually have more than one Application Menu on a panel. Then just use custom menus for the ones you want with non-standard menus. I don't know how easy it is to do, but it can't be altogether hard.

see: [http://standards.freedesktop.org/menu-spec/1.0/](http://standards.freedesktop.org/menu-spec/1.0/)

Thank you! I wanted as much to learn more about where files are located.

---

### Post by vasa1 on 2012-05-18
> **Manmadegod said:**
> Thank you! I wanted as much to learn more about where files are located.
[http://docs.xfce.org/](http://docs.xfce.org/)

---

### Post by LewisTM on 2012-05-18
Install xfce4-goodies and you will get a 'Places' item you can insert in your top panel. Set it to show no icon, only 'Places' and you've got yourself your Places Menu back.

Your System menu can be a custom launcher that runs xfce4-settings-manager or rolls down to show a collection of system utilities. In Xfce the system tools are typically distributed in the Settings and System application submenus. If you open you launcher properties dialog you can then drag-and-drop items from the main menu onto it.
Try doing that in GNOME!

Cheers!

---

