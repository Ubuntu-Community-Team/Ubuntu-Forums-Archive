---
title: "Rhythmbox won't start"
date: 2011-08-20
forum: General Help
---

### Post by bayvista on 2011-08-20
Ubuntu 10.04 RB won't start first time but starts second??? Any ideas?

---

### Post by pqwoerituytrueiwoq on 2011-08-20
what does it say in the terminal when you try to start it?
this should reset the rhythmbox (delete all settings)
```
rm -rf /home/$USER/.gconf/apps/rhythmbox/*
rm -rf /home/$USER/.local/share/rhythmbox/*
rm -rf /home/$USER/.cache/rhythmbox/*
```

---

