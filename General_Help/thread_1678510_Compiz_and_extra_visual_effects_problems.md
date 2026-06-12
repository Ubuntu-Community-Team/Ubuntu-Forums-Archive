---
title: "Compiz and extra visual effects problems"
date: 2011-01-30
forum: General Help
---

### Post by Dead Storage on 2011-01-30
Ok I am really confused, I have been using compiz ever since i installed ubutu about two weeks ago but recently whenever I restart my computer it defaults to no visual effects, and then when i try to turn it on it tells me desktop effects could not be enabled, I know I can do it because I have been.

I am on Ubuntu 10.04LTS Lucid Lynx, Kernal: 2.6.32-28 Generic
My laptop is a toshiba L505-S5988

Please any help would be greatly appreciated

---

### Post by realzippy on 2011-01-30
What happens when running  in terminal
```
compiz --replace
```
If it works put the command in System/Settings/StartupApplications,and welcome to Ubuntuforums!

---

### Post by Dead Storage on 2011-01-30
```
compiz (core) - Error: Another composite manager is already running on screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

(metacity:18128): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
Window manager warning: Log level 16: Another compositing manager is running on screen 0
```

---

### Post by Dead Storage on 2011-01-30
a

---

### Post by Dead Storage on 2011-01-30
> **realzippy said:**
> What happens when running  in terminal
```
compiz --replace
```If it works put the command in System/Settings/StartupApplications,and welcome to Ubuntuforums!

Also that made my windows mess up, the minimize maximize and close buttons where gone

---

### Post by Dead Storage on 2011-01-30
And now its just nowt working at all no matter how many times I restart

---

### Post by realzippy on 2011-01-30
Have you installed/updated anything lately?Desktop theme?

---

### Post by Dead Storage on 2011-01-30
> **realzippy said:**
> Have you installed/updated anything lately?Desktop theme?
I actually just figured it out, xcompmgr was running and for some reason it was keeping it from using compiz and all the 3d effects

---

