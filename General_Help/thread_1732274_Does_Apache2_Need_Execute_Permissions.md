---
title: "Does Apache2 Need Execute Permissions?"
date: 2011-04-18
forum: General Help
---

### Post by ubila on 2011-04-18
Hello all :)

Just wondering if Apache2 needs execute permissions for webhosting? Running PHP pages.

Wanting to know if its safe for me to change my hosted folders permissions to 740 cheers

---

### Post by duanedesign on 2011-04-18
chmod 644 if the files are html
chmod 655 if they need to be executed like perl scripts, php scripts

---

