---
title: "Nautilus broken after hacking on glib"
date: 2010-11-27
forum: General Help
---

### Post by LanoxxthShaddow on 2010-11-27
I am having a problem with nautilus since today. I was hacking on glib and trying a few things with the way stuff gets mounted, after a while i noticed that nautilus was seriously broken. Network, Computer, and all volumes are not displayed anymore. I wanted to revert to the original state, and tried to reinstall glib, gvfs and nautilus with the packet manager, but it didnt change anything. Does anyone have an idea how i can restore everything to normal. I tried running nautilus as root or reinstall gvfs-backend and other things but it didnt work. Cheers

---

### Post by sikander3786 on 2010-11-27
Did you try purging and reinstalling Nautilus?

```
sudo apt-get remove --purge nautilus
```

```
sudo apt-get install nautilus
```

You'll lose any custom settings/bookmarks that way I think.

---

### Post by LanoxxthShaddow on 2010-11-27
tried but didnt work, trash is also broken btw.

---

### Post by Locke_99GS on 2010-11-27
Reinstall any of the bits you were hacking on; ex: *sudo apt-get install --reinstall libglib2.0-bin libglib2.0-bin*

---

### Post by LanoxxthShaddow on 2010-11-28
I reinstalled everything that is related to glib: sudo aptitude reinstall libglib2.0-0 libglib2.0-{bin,cli,data}  no change in nautilus, it still doesnt display most of my partitions except those already mounted and also doesnt allow me to browse network or computer  strange... I used "make;sudo make install; sudo ldconfig" in the glib directory downloaded from the git repository and checked out tag 2.26.0  any more ideas?

---

### Post by deserthowler on 2010-11-28
You need to completely purge and make a fresh install of the components.

Earl

---

### Post by LanoxxthShaddow on 2010-11-29
Thanks for the input. I was just about to try your suggestion and purge everything when i got the idea to try and run "sudo make uninstall" in the glib git folder. I cannot explain how this is different from reinstalling everything through the package manager, but for some reason it worked and now everything is back to normal.  Thanks alot to everyone. Cheers Sebastian

---

