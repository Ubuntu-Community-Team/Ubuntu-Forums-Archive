---
title: "Change Start Icon On Gnome Panel?"
date: 2011-02-13
forum: General Help
---

### Post by Mikux on 2011-02-13
Recently updated to 10.10  Wondering if it's possible to change the start icon on the gnome panel?  

[IMG]http://www1.ubuntuforums.org/[IMG]http://i1020.photobucket.com/albums/af322/ArchMikux/snapshot1.png[/IMG][IMG]http://i1020.photobucket.com/albums/af322/ArchMikux/snapshot1.png[/IMG]

In the past I have been able to accomplish this by navigating to the theme's icon folder (usr/share/icons), replacing it with my new icon, updating the cache and restarting gnome.  That method doesn't seem to be working however.

Any idea?

---

### Post by jwcalla on 2011-02-13
I used the Ubuntu Tweak application to do it.  The option in the application is under Desktop -> GNOME Settings -> Menu Settings.

I think you need to add [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) to the Software Sources to pick up Ubuntu Tweak in Synaptic.

---

### Post by jerrrys on 2011-02-13
you can also go to gconf/apps

[ATTACH]183339[/ATTACH]

---

### Post by linuxsyst on 2011-02-13
Here [http://www.omgubuntu.co.uk/2010/10/customizing-ubuntu-10-10-with-a-dock-new-icon-theme-effects-global-menu-and-more/](http://www.omgubuntu.co.uk/2010/10/customizing-ubuntu-10-10-with-a-dock-new-icon-theme-effects-global-menu-and-more/) is good link to change it
please answer if works.

---

### Post by Mikux on 2011-02-13
> **jwcalla said:**
> I used the Ubuntu Tweak application to do it.  The option in the application is under Desktop -> GNOME Settings -> Menu Settings.

I think you need to add [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) to the Software Sources to pick up Ubuntu Tweak in Synaptic.

Wow... didn't even realize Ubuntu Tweak had that option (I rarely venture away from the App Center & Package Cleaner).  Worked like a charm, thanks.

> **jerrrys said:**
> you can also go to gconf/apps

[ATTACH]183339[/ATTACH]

I should have mentioned that I already gave that a try, as well as trying to navigate to the theme and manually changing the icon located in that folder.  No luck with either method.  Even after successfully changing it using Ubuntu Tweak, I can't pinpoint what icon file was actually changed.  Gconf doesn't show that I am using a custom icon, and as far as I can tell nothing within the theme folder has been changed.

---

### Post by Mikux on 2011-02-14
Looks like after a restart, the icon changed back to it's theme default.  Tried changing it again using Ubuntu Tweak, and no luck.  UT shows the new icon as being in place, but no changes actually take effect.

Any ideas?

---

### Post by Claus7 on 2011-02-14
Hello,

how about this?
[http://ubuntuforums.org/showpost.php?p=9972796&postcount=1](http://ubuntuforums.org/showpost.php?p=9972796&postcount=1)

Regards!

---

### Post by Mikux on 2011-02-14
> **Claus7 said:**
> Hello,

how about this?
[http://ubuntuforums.org/showpost.php?p=9972796&postcount=1](http://ubuntuforums.org/showpost.php?p=9972796&postcount=1)

Regards!

Unfortunately no luck.

---

### Post by Mikux on 2011-02-14
Sorry for the double post, but it once again seems to be working through Ubuntu Tweak.  Restarted gnome, and the changes appear to be working.

Again, Gconf does not show that I am using a custom button, and I have no idea what file UT actually changed.

---

