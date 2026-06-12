---
title: "Export passphrase"
date: 2011-12-13
forum: General Help
---

### Post by thezood on 2011-12-13
I recently encrypted my home folder on my netbook running WattOS (Ubuntu 11.04 with LXCE) but I never got around to exporting my passphrase. I realize now that this is really stupid. I can't find a good instructions on how to do this afterwards, does anyone know?

EDIT: the way to do this is running:
```
ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase
```

---

