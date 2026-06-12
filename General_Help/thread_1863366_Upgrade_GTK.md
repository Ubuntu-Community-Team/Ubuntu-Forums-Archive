---
title: "Upgrade GTK?"
date: 2011-10-17
forum: General Help
---

### Post by galacticaboy on 2011-10-17
I am using Ubuntu 10.04LTS and it has GTK 2.x, can I upgrade that to GTK 3.x? If I can, how do I do it?

---

### Post by crdlb on 2011-10-18
Please forgive me for asking, but why? None of the GTK2 apps on your system will use it. GTK3 can be installed in parallel with GTK2, but it depends on a newer version of GLib that is not parallel-installable. Therefore, there's no way a PPA could have GTK3 without including an upgrade to GLib, which would be a bit crazy. You could, however, safely build GTK3 and all its dependencies from source and install them into a custom prefix like /opt/gtk3/, but I won't go into more detail unless you need it.

---

### Post by MonolithImmortal on 2011-10-18
You don't want to do that, trust me.

Also, crdlb hit the nail on the head.

---

