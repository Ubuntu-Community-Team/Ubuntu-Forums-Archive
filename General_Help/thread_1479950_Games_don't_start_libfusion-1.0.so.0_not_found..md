---
title: "Games don't start: libfusion-1.0.so.0 not found."
date: 2010-05-11
forum: General Help
---

### Post by guitarMan666 on 2010-05-11
I recently upgraded to Ubuntu 10.04 Lucid Lynx from the previous version. After doing so, all of the games I have installed that require 3D of any kind (and one that does not) refuse to start with an error similar to the following:
```

$ openarena
openarena: error while loading shared libraries: libfusion-1.0.so.0: cannot open shared object file: No such file or directory

```

The complete tests will be attached seperately. For the purpose of this post I tested DOSBox, Sauerbraten (Cube 2) and FrozenBubble. All fail to start and all complain about not finding libfusion-1.0.so.0. I cannot find that particular version installed but a newer version appears to be in place:
```

$ locate libfusion
/usr/lib/libfusion-1.2.so.0
/usr/lib/libfusion-1.2.so.0.8.0
/usr/lib/libfusion.a
/usr/lib/libfusion.so
/usr/lib/googleearth/libfusioncommon.so

```

I can't imagine so many games would be left with an old dependency and forced not to work. I made sure that the games I tested were all in the official repos and if I accidentally include one that isn't, please disregard it.

As an aside, Wine applications requiring 3D start just fine, like Star Wars: Jedi Outcast in OpenGL mode.

---

### Post by guitarMan666 on 2010-05-12
I used a possibly unwise workaround to fix this issue: I symlinked the new version to the name of the old version. Dirty, but the all start now.

---

