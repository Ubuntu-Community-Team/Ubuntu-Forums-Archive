---
title: "Choose Helper App in Firefox frustrating!"
date: 2012-04-18
forum: General Help
---

### Post by euphoric_anomaly on 2012-04-18
I used to have Movie Player (totem) set to play .pls files (streaming music), now it has Banshee as the default. I currently use Banshee for my MP3's but NOT for streaming music (because it never works when using banshee).

I go into firefox, click on the .pls I want to stream, and it asks me which app it should open with, I go to "Choose Another" and that's where I'm lost..

I have no idea where Movie Player is located, or what the filename is, mplayer? totem? etc

All I would like is an easy way to find where applications are installed when using Software Center, I'm sure this is a super-noob question you've seen 140000 times, but I'm still learning my way around Ubuntu and it's seemingly endless array of folders.

Any help would be greatly appreciated! 
Thanks!

---

### Post by HiImTye on 2012-04-19
/usr/bin/ is where you will find most executables installed via the apt family of package managers

if you are unsure you can always perform a search for it
```
tye@T:~$ find type f / 2> /dev/null | grep totem$
/usr/lib/totem
/usr/lib/totem/totem
/usr/share/doc/totem
/usr/share/menu/totem
/usr/share/omf-langpack/totem
/usr/share/gnome/help/totem
/usr/share/gnome/help-langpack/totem
/usr/share/omf/totem
/usr/share/totem
/usr/share/gtk-doc/html/totem
/usr/share/bug/totem
/usr/share/lintian/overrides/totem
/usr/bin/totem
/home/tye/.gconf/apps/totem
/home/tye/.config/totem
/home/tye/.local/share/totem
```

---

### Post by euphoric_anomaly on 2012-04-19
I found it! I looked in usr/bin/ and found totem (a tiny 13.3kB file), but it works fine now.
thank you so much!

---

