---
title: "ubuntu kernel not getting updated"
date: 2010-01-26
forum: General Help
---

### Post by drrampgi on 2010-01-26
in my friends computer kernel version is 2.6.31-18, but in my computer the version is 2.6.31-17 can anybody help to update?

---

### Post by feelshift on 2010-01-26
It seams the same version to me :popcorn:
Later edit:
You corrected the post.

Try
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by drs305 on 2010-01-26
The -18 kernel for karmic is currently only available in the 'proposed' repository. To get it through normal updates you change the repositories via Software Sources or Synaptic. Settings, Repositories, Updates and enable 'proposed' and reload. 

I would recommend you stay with the normal repositories, however, unless you have a specific need for the -18 kernel at this time. The *proposed* and *backports* repositories haven't been tested as thoroughly as the main Ubuntu repositories,

---

### Post by warfacegod on 2010-01-26
The current stable version is 17. 18 is still in testing. If you would like it, go to:

System> Admin.> Software Sources> Updates tab> Check Unsupported updates (karmic-backports)

Reload the list and then do an update.

---

