---
title: "How do I completely remove a program?"
date: 2010-01-15
forum: General Help
---

### Post by PDA1 on 2010-01-15
I want to completely remove Thunderbird (all versions) from my computer so I can do a re-install.

Synaptic will not remove all occurances of TB and I want off my machine...GONE.

Now, using terminal....is there an easy way to do it?

---

### Post by Portmanteaufu on 2010-01-15
> **PDA1 said:**
> I want to completely remove Thunderbird (all versions) from my computer so I can do a re-install.

Synaptic will not remove all occurances of TB and I want off my machine...GONE.

Now, using terminal....is there an easy way to do it?

Usually one would do:

```
sudo apt-get remove thunderbird
```

What is Synaptic leaving behind? Can you elaborate on what you've tried and what happened as a result?

---

### Post by PDA1 on 2010-01-15
Here's what I get with the "find" command---


root@earl-laptop:~# find / -name *thunderbird*
/var/cache/apt/archives/thunderbird-3.0_3.0.1~hg20091227r4573+nobinonly-0ubuntu1~umd1~karmic_i386.deb
/var/cache/apt/archives/thunderbird-3.0_3.0.2~hg20100114r4634+nobinonly-0ubuntu1~umd1~karmic_i386.deb
/var/cache/apt/archives/thunderbird-3.0_3.0.1~hg20100105r4589+nobinonly-0ubuntu1~umd1~karmic_i386.deb
/var/cache/apt/archives/thunderbird-3.0_3.0.1~hg20100104r4588+nobinonly-0ubuntu1~umd1~karmic_i386.deb
/var/cache/apt/archives/thunderbird_2.0.0.23+build1+nobinonly-0ubuntu1_i386.deb
/var/cache/apt/archives/thunderbird-3.0_3.0.2~hg20100111r4629+nobinonly-0ubuntu1~umd1~karmic_i386.deb
/var/cache/apt/archives/thunderbird-3.0_3.0.2~hg20100113r4631+nobinonly-0ubuntu1~umd1~karmic_i386.deb
/usr/lib/thunderbird
/usr/lib/thunderbird-3.0.2pre
/usr/share/thunderbird
/usr/share/doc/git-core/contrib/thunderbird-patch-inline
/usr/share/app-install/icons/mozilla-thunderbird-bidiui.xpm
/usr/share/app-install/desktop/thunderbird.desktop
/usr/share/app-install/desktop/mozilla-thunderbird-bidiui.desktop
/usr/share/app-install/desktop/thunderbird-quickfile.desktop
/usr/share/gtkpod/scripts/sync-thunderbird.sh
/usr/share/gtkpod/scripts/sync-thunderbird-nano.sh
/home/earl/Downloads/thunderbird-3.0.tar.bz2
/home/earl/.local/share/applications/thunderbird-3.0.desktop
/root/.mozilla-thunderbird
/root/.thunderbird
/root/.thunderbird-3.0
/root/.local/share/Trash/files/Thunderbird 3.0/thunderbird
/root/.local/share/Trash/files/Thunderbird 3.0/thunderbird/thunderbird
/root/.local/share/Trash/files/Thunderbird 3.0/thunderbird/thunderbird-bin
/root/.local/share/Trash/files/Thunderbird 3.0/thunderbird/defaults/pref/thunderbird-branding.js
/root/.local/share/Trash/files/Thunderbird 3.0/thunderbird/defaults/pref/all-thunderbird.js

---

### Post by ajgreeny on 2010-01-15
How did you install TB3?  If you did not use synaptic it will probably not be removed that way.  If it was a tarball source install you may need to go through the terminal to remove it, but you will need to look further for an answer than me, I'm afraid.

I have tried TB3, but ran it from the tarball I downloaded from mozilla, which was not source files, but had a binary in the archive which worked when double clicked; there was no need to install the app, I just ran it direct.

---

### Post by warfacegod on 2010-01-15
What about:

```
sudo apt-get purge thunderbird
```

---

### Post by Uncle Spellbinder on 2010-01-15
I believe this will do it...

```
sudo apt-get remove --purge PACKAGE NAME
```

---

### Post by Leppie on 2010-01-15
i believe the following command would remove all versions of tb (altogether with their config files):
```
sudo apt-get purge thunderbird*
```

---

