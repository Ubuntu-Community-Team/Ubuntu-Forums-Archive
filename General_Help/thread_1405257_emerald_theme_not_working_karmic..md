---
title: "emerald theme not working karmic."
date: 2010-02-12
forum: General Help
---

### Post by soryu on 2010-02-12
emerald theme wont enable. i ran emerald --replace in terminal nothing
i replaced command in compiz nothing
i added emerald as a start up nothing.
right now there are no window borders.
window decorations are enabled.
what am i missing?

---

### Post by gjoellee on 2010-02-12
> **soryu said:**
> emerald theme wont enable. i ran emerald --replace in terminal nothing
i replaced command in compiz nothing
i added emerald as a start up nothing.
right now there are no window borders.
window decorations are enabled.
what am i missing?

In terminal use:

```
ccsm
```Compiz' confid window pops up. If "Window Decoration" are already checked, recheck it. Try again. It may also be because your card does not have a driver, or can't run compiz.

You may also try fusion-icon:

```
sudo apt-get install fusion icon
```

and run it:

```
fusion-icon
```

a icon in your notification area should appear. Right click on it to see the options you have. Set Emerald to window decorator.

---

