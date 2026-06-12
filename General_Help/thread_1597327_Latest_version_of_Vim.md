---
title: "Latest version of Vim"
date: 2010-10-15
forum: General Help
---

### Post by benbelly on 2010-10-15
I updated to 10.10 last night hoping that the latest version of vim would come with it, but I was disappointed to find vim 7.2 instead of 7.3. Does anyone know of a source for updated vim packages?

I don't like to manually install these things as I tend to get things in a funny state, but I'm pretty excited about some of the new features.

Thanks,
-Ben

---

### Post by blueridgedog on 2010-10-15
You could search the web for a .deb file (debian is using 7.3 [http://packages.debian.org/sid/vim-common](http://packages.debian.org/sid/vim-common)) or install from source.  For Vim, I recommend source install.

---

### Post by crichard on 2010-10-15
Yes, Install it from source. It's the way to go.. While compiling, if it asks about missing terminal library, try to install this package   libncurses5-dev 
```
sudo apt-get install libncurses5-dev
```

---

