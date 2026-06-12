---
title: "Installing synaptic"
date: 2010-09-04
forum: General Help
---

### Post by jcolyn on 2010-09-04
I much prefer synaptic over Kpackage and want to install it.

I know to do so I will do ```
sudo apt-get install synaptic
``` but will I need to uninstall Kpackage first or wait till synaptic is installed??

---

### Post by David Andersson on 2010-09-04
> **jcolyn said:**
> I much prefer synaptic over Kpackage and want to install it.

I know to do so I will do ```
sudo apt-get install synaptic
``` but will I need to uninstall Kpackage first or wait till synaptic is installed??

I think the Kpackage tool is the "kpackagekit" package. According to the dependencies you do not need to uninstall it when you install Synaptic. However, you cannot *run* them simultaneously (or run any of them simultaneously with apt-get). They will complain about the others running if you try.

---

