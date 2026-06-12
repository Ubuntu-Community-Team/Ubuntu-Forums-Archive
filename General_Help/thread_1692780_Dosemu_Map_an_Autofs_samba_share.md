---
title: "Dosemu: Map an Autofs samba share?"
date: 2011-02-21
forum: General Help
---

### Post by swanee on 2011-02-21
I have a networked windoze drive mounted through autofs as /mnt/di, Putting a link in ~/dosemu/drives as e->/mnt/di, then dosemu errors on startup. But if I make /mnt/di a directory, with the autofs symlink contained within it, then dosemu fires up okay, showing that E:\di contains all of the contents of the desired drive. However, the dos app which I want to run needs to see, eg E:\foo, not E:\di\foo. It only deals with top-level dirs. How can I proceed?

TIA,
Scott.

---

