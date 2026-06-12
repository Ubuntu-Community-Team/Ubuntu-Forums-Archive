---
title: "Kernel Not Auto Updating..."
date: 2009-12-27
forum: General Help
---

### Post by ephman on 2009-12-27
hi,

any help would be really appreciated.  so for some reason all packages i have installed seem to upgrade just fine.  except for the kernel.  currently running 9.10 x64. and i'm still running 2.6.31-14-generic.  how can i get the kernel to auto update again?

thanks,

ephman

---

### Post by ephman on 2009-12-29
sorry for the bump.

---

### Post by oldos2er on 2009-12-29
Open Software Sources (via menus System, Administration), click Updates, Karmic proposed. Close Software Sources, reload sources.list, and you should have some newer kernels available to install.

---

### Post by ephman on 2010-01-23
didn't work ;( any other ideas?

thanks,

ephman

---

### Post by drs305 on 2010-01-23
Do you have "linux-image" with no version information selected in Synaptic? That should retrieve the latest kernel; of course the operative word is "*should*.
 
You can also try this in a terminal window, which may provide an informative message if it doesn't install:
```

sudo apt-get install linux-image

```

Finally, are you sure it is not installed and just not being used?  Again, you can check Synaptic. Type "2.6.31-" in the search window, press the small arrow to the left of the Packages header to move the installed packages to the top of the list, and see which "linux-images-2.6.31..." are installed.

---

### Post by ephman on 2010-01-23
well i manually updated the kernel.  no worries.  not the end of the world.  yep i was running the original kernel that 9.10 shipped with.  

thanks,

ephman

---

