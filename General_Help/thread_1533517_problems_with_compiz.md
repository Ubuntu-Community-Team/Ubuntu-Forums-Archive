---
title: "problems with compiz"
date: 2010-07-18
forum: General Help
---

### Post by Messyhair42 on 2010-07-18
for some reason compiz has stopped working, on startup or otherwise. i've done nothing to change it and it was working fine 24 hours ago. i noticed it when i was having problems with VLC and Gnome Do. i'm not too concerned b/c i'm upgrading to Lucid in the very near future [new installation] but i'd like to understand what's happening.

---

### Post by potat on 2010-07-18
Try running 
```

$ nohup compiz --replace &
(wait a few seconds...)
$ cat nohup.out

```

in Terminal. What output do you get?

---

### Post by Messyhair42 on 2010-07-18
both commands give me
```
bash: $: command not found

```

---

### Post by Darkness Des on 2010-07-18
Erm, don't enter the dollar sign. That's what people put to signify the prompt, which looks like ```
username@computername~$
```So what you should do is this
```
nohup compiz --replace &
(wait a few seconds...)
cat nohup.out
```

---

### Post by Messyhair42 on 2010-07-18
```
nohup: ignoring input and appending output to `nohup.out'
```
and the screen flickered off for a moment
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator

```
compiz effects seem to be working now

---

