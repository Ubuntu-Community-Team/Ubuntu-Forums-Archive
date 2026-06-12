---
title: "accidentally deleted /etc/modprobe/blacklist.conf"
date: 2010-11-21
forum: General Help
---

### Post by tarverator on 2010-11-21
Shortly after installing Ubuntu 10.10, I accidentally deleted /etc/modprobe/blacklist.conf

Before I foolishly zapped it, I glanced at it for a second and noticed that it listed maybe half a dozen modules and comments explaining why they were blacklisted. Is this file dynamically generated depending on hardware, or the same across the distribution?

How can I restore this file?

---

### Post by mc4man on 2010-11-21
I would say it's static per ubuntu release (baring updates
You could try re-installing module-init-tools from synaptic (don't remove !
Likely it won't restore the file, if not go here, download the package for your system
[http://packages.ubuntu.com/maverick/module-init-tools](http://packages.ubuntu.com/maverick/module-init-tools)
Then r. click on - Extract here
Browse in the extracted folder to /etc/modprobe.d and you can copy back

A useful search place is here - bottom section searches file names, returns  packages found in.
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by tarverator on 2010-11-21
Thanks! I got the file, which looked as I remembered it, and I have restored it. I even remembered to change the group and owner from my user to root.  :)

---

