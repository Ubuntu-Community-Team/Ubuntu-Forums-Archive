---
title: "gnome-panel missing"
date: 2011-01-11
forum: General Help
---

### Post by snowmanman on 2011-01-11
I installed ubuntu netbook edition on my desktop (from the Ubuntu  Software Center) to test out Unity. It looked pretty cool, but every  time I went to the sidebar it flashed black. I decided I didn't want to  fiddle with it too much to get it working so I uninstalled the  ubuntu-netbook package. Mutter was still hanging around though (and  lot  of other things I assume) so I uninstalled that as well. Now  gnome-panel is gone and I don't know how to get it back. Any way to  uninstall all those packages and put it back?

---

### Post by TeoBigusGeekus on 2011-01-11
Press alt+f2 and give
```
gnome-terminal
```
to bring up the terminal.
Then
```
gnome-panel
```
in terminal, to see if you can get your panel back.
If that doesn't work, try reinstalling the whole gnome desktop
```
sudo apt-get install -reinstall gnome-desktop
```

---

