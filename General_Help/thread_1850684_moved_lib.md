---
title: "moved /lib"
date: 2011-09-27
forum: General Help
---

### Post by trorion on 2011-09-27
OK, meant ```
mv -v ./lib /var/www/
``` but forgot that pesky little .

so now /lib is at /var/www/lib which does not do well, how do I reset bin/bash (note bash) so I can move /lib back..since bin/bash looks in /lib for the mv command (and cp and well, most commands)

oh, not using X so I can't use and X programs; not that they would work without lib's.

---

### Post by dcstar on 2011-09-27
> **trorion said:**
> OK, meant ```
mv -v ./lib /var/www/
``` but forgot that pesky little .

so now /lib is at /var/www/lib which does not do well, how do I reset bin/bash (note bash) so I can move /lib back..since bin/bash looks in /lib for the mv command (and cp and well, most commands)

oh, not using X so I can't use and X programs; not that they would work without lib's.

Boot off a Live CD/USB, mount the disk and do it that way.

---

