---
title: "What happened to my widget layer?"
date: 2010-11-05
forum: General Help
---

### Post by rugbert on 2010-11-05
I just installed 10.10 and was setting everything up and noticed that after installing screenlets, I dont have the Widget Layer options in CCSM.

Whered it go?

---

### Post by rugbert on 2010-11-06
turns out the widget layer plugin was not installed, so i removed the CCSM via software center and installed it via terminal with :
```

sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-main compiz-fusion-plugins-extra emerald librsvg2-common

```

That gave installed the plugin and CCSM but I can only edit settings by launching it in terminal and sudoing it.

AND the key command to launch the layer doesnt work :/

---

### Post by Tryfon on 2010-11-16
Just open the synaptic package manager and install the extra plugins for compiz.

---

