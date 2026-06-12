---
title: "How to upgrade kubuntu?"
date: 2010-02-26
forum: General Help
---

### Post by Zeemvel on 2010-02-26
Hi,

I changed from Ubuntu to Kubuntu by installing KDE. I'm not sure if I have Ubuntu or Kubuntu now because at login I can choose between both desktops.

Anyway, when using Gnome, about once a week it asked for upgrades, and then did this all in the background.

Now with KDE, this doesn't work anymore. At some point there came a screen that was similar to that of Gnome, except if I pressed ok to update and entered my password, it crashed and brought up the KDE crash handler. Sorry I don't remember the name of this updater.

So anyway, how can I bring my (K)Ubuntu up to date now?

Thanks.

---

### Post by zvacet on 2010-02-26
See [this.]("https://help.ubuntu.com/community/Repositories/Kubuntu")Second  way is with synaptic ( I think you have it because you have Gnome installed)**>refresh>mark all updates**.You can update from terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

