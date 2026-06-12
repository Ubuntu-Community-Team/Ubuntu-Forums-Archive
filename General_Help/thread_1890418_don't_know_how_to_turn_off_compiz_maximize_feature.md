---
title: "don't know how to turn off compiz maximize feature"
date: 2011-12-03
forum: General Help
---

### Post by youWho on 2011-12-03
I'm not sure where to post this; hopefully here is fine.

I've been trying to figure out where in the world to configure the effect in Compiz that causes the window to maximize when it happens to meet the top of the screen---I don't want it to do that. Short of going back to using Metacity, does anybody know a short answer please?? Believe me, I've searched far and wide, and the biggest problem is that the search results cover about 3 million quasi-related features. Why is there no simple help document for Compiz (or is there and I missed it)?

I'm using Ubuntu Studio natty, 64 bit, non-Unity

---

### Post by bluexrider on 2011-12-03
here is a listing of the plug-ins and what they do:

[http://wiki.compiz.org/CompizFusionPlugins](http://wiki.compiz.org/CompizFusionPlugins)

---

### Post by JRV on 2011-12-03
Open a terminal and enter the following commands:

```

sudo apt-get install compizconfig-settings-manager
ccsm

```

Uncheck "Grid" near the bottom in the Window Management section.

---

### Post by youWho on 2011-12-03
Thanks a lot!!! Whew.

---

### Post by JRV on 2011-12-03
Glad to help, please mark your thread solved.

---

