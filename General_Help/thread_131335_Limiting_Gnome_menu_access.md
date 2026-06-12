---
title: "Limiting Gnome menu access"
date: 2006-02-16
forum: General Help
---

### Post by Revolution on 2006-02-16
I just recently set up Edubuntu for the kids to use but I'm finding they love to explore.
Is there a way to limit access to menus/programs that I dont want them using?

Can I password access the normal Gnome menu structure and just let them use a special "Education" menu with their programs?

Cheers.

---

### Post by ngms27 on 2006-02-16
I'm interested is this aswell.

Is there a solution?

---

### Post by slux on 2006-02-16
If they have their own usernames you could simply use the menu editor to delete the entries you don't want shown. That'd be the easiest solution and other users will still have full menu access.

You could also remove the entries from the system-wide menu configuration files and only access them by manually typing the program names (or your own launchers in your profile)

I guess one option would be also simply to use file permissions to limit the execution rights for the apps you want to disable but then you need to make sure that apt plays nice or your permission changes could get wiped in a package upgrade.

---

