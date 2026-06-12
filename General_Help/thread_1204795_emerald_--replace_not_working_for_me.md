---
title: "emerald --replace not working for me"
date: 2009-07-05
forum: General Help
---

### Post by 7raTEYdCql on 2009-07-05
I just recently installed ccsm and emerald theme manager. In my startup sessions i added emerald --replace. But emerald doesn't get enabled on startup. When manually using it in terminal, nothing happens.

---

### Post by t4thfavor on 2009-07-06
Does the terminal display any messages, if so they could be clues to what your problem is. Oh, and don't run it as root (no sudo).

---

### Post by 7raTEYdCql on 2009-07-06
I am not running as root. And the terminal doesn't show any reponse when i try the command.

---

### Post by ad_267 on 2009-07-06
You can change the window decorator command to "emerald --replace" in the compiz configuration manager under the window decoration plugin. That's the way I'd do it rather than adding emerald --replace to the list of startup applications.

Have you installed and selected an emerald theme?

---

### Post by 7raTEYdCql on 2009-07-06
```
mehrzad@mehrzad-laptop:~$ emerald --replace
^C
mehrzad@mehrzad-laptop:~$ 

```

This is my terminal after half an hour of running the command.

---

### Post by 7raTEYdCql on 2009-07-06
More so, even changes that i make in ccsm, aren't applied to my desktop. The only changes that work for me are the ones i do on right clicking(on desktop) ->Change Desktop Background -> Theme.

I can't change my theme from any other source. Can someone please help, i am bored with the looks of my ubuntu.

---

### Post by ad_267 on 2009-07-06
Well emerald won't work if Compiz isn't running. Have you enabled compiz from System - Preferences - Appearance - Visual Effects? What do you get if you run "compiz --replace &" in a terminal?

---

### Post by 7raTEYdCql on 2009-07-07
```
mehrzad@mehrzad-laptop:~$ compiz compiz --replace &
Checking for Xgl: [1] 4012
mehrzad@mehrzad-laptop:~$ not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'compiz'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format



```

---

