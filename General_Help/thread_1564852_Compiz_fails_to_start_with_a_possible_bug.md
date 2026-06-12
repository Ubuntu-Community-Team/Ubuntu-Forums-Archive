---
title: "Compiz fails to start with a possible bug"
date: 2010-08-31
forum: General Help
---

### Post by nmvictor on 2010-08-31
Hi, i have been using compiz on my laptop loaded with Lucid,without any problems.Recently i reinstalled lucid but now i dont have a compositing manager, I try > compiz --replace in the terminal and i get the following:
```
nmvictor@nmvictor-linuxbox:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
[ERROR]: Option "pulse" already defined
[ERROR]: Option "blur_speed" already defined
[ERROR]: Option "focus_blur_match" already defined
[ERROR]: Option "focus_blur" already defined
[ERROR]: Option "alpha_blur_match" already defined
[ERROR]: Option "alpha_blur" already defined
[ERROR]: Option "filter" already defined
[ERROR]: Option "gaussian_radius" already defined
[ERROR]: Option "gaussian_strength" already defined
[ERROR]: Option "mipmap_lod" already defined
[ERROR]: Option "saturation" already defined
[ERROR]: Option "occlusion" already defined
[ERROR]: Option "independent_tex" already defined
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
i915_program_error: Exceeded max nr indirect texture lookups

Launching fallback window manager
```

---

### Post by juil on 2010-08-31
Open Software Centre
Type compiz
Install compiz

or

> sudo apt-get install compiz compizconfig-settings-manager

---

### Post by nmvictor on 2010-08-31
> **juil said:**
> Open Software Centre
Type compiz
Install compiz

or
thanks but compiz is already the newest version in my system, as well as compiz-settings-manager. I have removed them for re installation but still experiencing the same.

---

### Post by juil on 2010-08-31
Sorry, can you be more clear?
Experiencing the same what? You don't have compiz on your system after the
upgrade? You don't have compiz even after re-installing?

---

### Post by drewsus on 2010-11-30
> **juil said:**
> Sorry, can you be more clear?
Experiencing the same what? You don't have compiz on your system after the
upgrade? You don't have compiz even after re-installing?

I assume he has the same error as previously. I too now have this error after applying a profile from another computer. Never had a problem doing that in the past.

---

