---
title: "Disabling/Undoing Compiz changes turned on by &quot;Ubuntu Tweak&quot;"
date: 2011-06-13
forum: General Help
---

### Post by divyamistry on 2011-06-13
I'm on Ubuntu Natty.

I just got the latest Ubuntu Tweak 0.5.14, and decided to turn on the Compiz effects from its "Compiz Settings". Turning it on installed some packages, but I'm not sure which ones. I want to "undo" the changes made from it, but the software doesn't have that option. I looked at [http://ubuntu-tweak.com/about/](http://ubuntu-tweak.com/about/) and their blog, but haven't been able to find the answer.

Does anyone know how to do either of the following:
(1) turn off compiz from Unity or Gnome built into Natty (earlier Ubuntu had "Visual Effects" tab in Appearance settings, which is gone in Natty, so I'm not sure where to go)

(2) find out which packages were installed by "Ubuntu Tweak 0.5.14" when user selected to turn on Compiz Effects.

PS: apt-get remove compiz   removed compiz, unity, gnome-desktop and couple other packages, so I did apt-get install compiz unity gnome-desktop*

I actually don't care which packages stay on the system, I just need to be able to turn on/off Compiz, I guess.

---

### Post by scottstensland on 2011-08-18
any package change (install/update/remove) cuts an entry  /var/log/dpkg.log

---

