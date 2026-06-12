---
title: "Error building gnome shell"
date: 2011-01-23
forum: General Help
---

### Post by andymorton on 2011-01-23
I'm following this guide on how to build gnome shell  - [http://live.gnome.org/GnomeShell#Building](http://live.gnome.org/GnomeShell#Building)

but I've encountered the following error 

 - ```

make: *** [all] Error 2

*** Error during phase build of atk: ########## Error running make   *** [6/33]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"

```

I'm not sure what I should do next. Any help would be greatly appreciated.

Thanks 
andy

---

### Post by Spr0k3t on 2011-01-23
I haven't built gnome-shell yet, but from my personal experience, try removing all additional 3D elements of the desktop if you haven't already.

```
sudo metacity --replace &
```

Then continue with your build.

---

### Post by andymorton on 2011-01-23
> **Spr0k3t said:**
> I haven't built gnome-shell yet, but from my personal experience, try removing all additional 3D elements of the desktop if you haven't already.

```
sudo metacity --replace &
```

Then continue with your build.



Hi, 

Thanks! But I'm still getting the same error. Would any of the options in the code in my previous post help at all? 
:)

---

### Post by Spr0k3t on 2011-01-23
I'd try a rerun... if that comes up with the same error, ignore the error and see if you can procede.  Sometimes the build scripts work without problems, where others have issues tied to differences in the directory structure.

---

### Post by andymorton on 2011-01-23
Ok, thanks. I'll give it a shot. 

andy

---

### Post by andymorton on 2011-01-23
> **Spr0k3t said:**
> I'd try a rerun... if that comes up with the same error, ignore the error and see if you can procede.  Sometimes the build scripts work without problems, where others have issues tied to differences in the directory structure.

Hi, I managed to get it working! :D

Thanks for your help, I appreciate it!!

andy

---

