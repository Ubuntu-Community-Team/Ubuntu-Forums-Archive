---
title: "Help! nautilus won't start"
date: 2010-09-29
forum: General Help
---

### Post by psycho5 on 2010-09-29
Hi, I installed ubuntu tweaks, and thought it I installed nautilus-wallpaper, then I noticed I can't browse any folders, my desktop icons are gone. 

So i uninstalled nautilus-wallpaper and rebooted the pc, still there are no icons. The mouse cursor keeps spinning.

I tried sudo nautilus in terminal it gives me error

```

sudo nautilus
nautilus: symbol lookup error: nautilus: undefined symbol: g_application_get_type
:~$

```

what do I do? luckily I can run apps through the menu and alt+f2 but can't browse my files.

---

### Post by SlugSlug on 2010-09-29
```
sudo apt-get remove --purge nautilus && sudo apt-get update && sudo apt-get install nautilus 
```

---

### Post by psycho5 on 2010-09-29
I was about to do that, then I realized I had 350MB of updates, nautilus got updated and everything's okay :popcorn:

---

