---
title: "odd rhythmbox installation error"
date: 2010-09-11
forum: General Help
---

### Post by princeofnam on 2010-09-11
E: /var/cache/apt/archives/rhythmbox-plugins_0.12.8-0ubuntu7_i386.deb: trying to overwrite '/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png', which is also in package faenza-icon-theme 0



no idea what that means or how to   go around it

---

### Post by jamesisin on 2010-09-11
You might want to give information about how you came to this error.

---

### Post by inameiname on 2010-09-11
Seems the icon 'as-icon.png' is in both the packages, rhythmbox-plugins_0.12.8-0ubuntu7_i386 and faenza-icon-theme. As default, package installations do not allow you to overwrite a file if it is in another package. Sometimes this happens. 

You could remove the faenza-icon-theme. Or easy workaround is to force install rhythmbox-plugins_0.12.8-0ubuntu7_i386. It just overwrites that one file. Can force install it by:

sudo aptitude download rhythmbox-plugins

...and then:

sudo dpkg -i --force-overwrite "/path/to/rhythmbox-plugins_0.12.8-0ubuntu7_i386.deb"

---

