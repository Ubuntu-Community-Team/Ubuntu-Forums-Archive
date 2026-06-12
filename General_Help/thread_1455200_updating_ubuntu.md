---
title: "updating ubuntu?"
date: 2010-04-15
forum: General Help
---

### Post by jinjin on 2010-04-15
ok so ubuntu 10.04 is coming and im currently using ubuntu 9.10, if i want ubuntu 10.04, do i just update the kernel? will it be available in the update manager?

or do i have to dl ubuntu 10.04 and remove 9.10 and install 10.04 like that?
 
thanks in advance!

---

### Post by lisati on 2010-04-15
Whenever there's a new release, the update manager will offer to upgrade for you, but won't do so without your permission.

---

### Post by jinjin on 2010-04-15
so i don't have to download the new version from the site and reinstall everything right?

just use the update manager and it auto updates to new version?

---

### Post by maddg3241 on 2010-04-15
ya you just got to update normally but stay there well it does it

---

### Post by zvacet on 2010-04-15
Another method is upgrading with alternate CD.In this case you always have CD if something goes wrong.But,yes you can upgrade from update manager.

---

### Post by garvinrick4 on 2010-04-15
Just the way I like to upgrade it all at once. A lot of different ways.


sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

