---
title: "Cannot click in Flash (from Adobe)"
date: 2009-11-24
forum: General Help
---

### Post by lian1238 on 2009-11-24
Before you tell me to "GOOGLE IT!", please hear me out.

I installed flash from the deb file from Adobe.

I cannot add
```

export GDK_NATIVE_WINDOWS=1

```
to /usr/lib/nspluginwrapper/i386/linux/npviewer
because I do not have the file and do not have nspluginwrapper installed.

System:
Flash 10.0 r32
Firefox 3.5.5
Ubuntu 9.10 32bit
Nvidia driver ver. 190.42 with NVidia GT240M.
Compiz and Emerald Running.

---

### Post by Giblet5 on 2009-11-24
Try ```
sudo apt-get install flashplugin-nonfree
```

The Ubuntu repositories are bigger than you presumed.

---

### Post by lian1238 on 2009-11-24
Okay, I just did it. And restarted firefox. But it still happens.

---

### Post by hwttdz on 2009-11-24
Giblet, won't lian1238 also have to remove the downloaded version of flash?

See post #69 here [http://ubuntuforums.org/showthread.php?t=1333876](http://ubuntuforums.org/showthread.php?t=1333876)

---

### Post by spongypants23 on 2009-11-24
Edit: Nevermind.

---

