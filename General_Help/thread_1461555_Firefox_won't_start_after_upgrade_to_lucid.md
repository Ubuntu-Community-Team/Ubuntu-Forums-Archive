---
title: "Firefox won't start after upgrade to lucid?"
date: 2010-04-24
forum: General Help
---

### Post by Redundant Username on 2010-04-24
Heres' what I get when I try to run it from the terminal.
```
anthony@ubuntu:~$ firefox
LoadPlugin: failed to initialize shared library /home/anthony/.mozilla/plugins/libflashplayer.so [/home/anthony/.mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
LoadPlugin: failed to initialize shared library /usr/lib/firefox-addons/plugins/libflashplayer.so [/usr/lib/firefox-addons/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
Attempting to load the system libmoon 
Segmentation fault

```

---

### Post by Ayuthia on 2010-04-24
It looks like you installed the wrong version of flash.  Did you install flash from the repositories or are you getting it from Adobe?  If it is from Adobe, my guess is that you grabbed the 32-bit version instead of the 64-bit beta version.

---

### Post by Redundant Username on 2010-04-24
I didn't install any new version of flash, I installed flash from the repositories. I think I may have deleted some folders during the upgrade to 10.4 to make space, since my drive was full.

---

### Post by Ayuthia on 2010-04-24
I would try backing up the libflashplayer.so files from those two directories and then remove them and try starting firefox again.  If it works, then you can copy them back, uninstall flash, and try installing it again.

Are you using 64-bit or 32-bit?  If you are using 64-bit, it might also be using nspluginwrapper.  You might check:
```
nspluginwrapper -l
``` to see if there is a list of where it stores the 32-bit flash.

---

### Post by Redundant Username on 2010-04-24
I'm using 64-bit Lucid. ```
anthony@ubuntu:~$ nspluginwrapper -l
/usr/lib/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-installer/libflashplayer.so
  Wrapper version string: 1.2.2
/usr/lib64/mozilla/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-installer/libflashplayer.so
  Wrapper version string: 1.2.2
/usr/lib/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-installer/libflashplayer.so
  Wrapper version string: 1.2.2
/usr/lib64/firefox/plugins/flashplugin-alternative.so
  Original plugin: /usr/lib/flashplugin-installer/libflashplayer.so
  Wrapper version string: 1.2.2

```

---

### Post by Ayuthia on 2010-04-24
Have you tried making the backup copies of libflashplayer.so and taking them out of those directories and restarting firefox?

---

### Post by lovinglinux on 2010-04-25
Reinstall the latest flash 64bit. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Anonymousable on 2010-04-26
The problem is actually with Novell Moonlight  - I had the same. Uninstall libmoon and try again.

---

