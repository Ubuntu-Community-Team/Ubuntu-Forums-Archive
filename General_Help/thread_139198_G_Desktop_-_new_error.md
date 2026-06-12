---
title: "G Desktop - new error"
date: 2006-03-03
forum: General Help
---

### Post by armyrebel on 2006-03-03
I think for sure that I have the dependency's that i need... 

ite-packages
checking /usr/include/python2.4/Python.h usability... yes
checking /usr/include/python2.4/Python.h presence... yes
checking for /usr/include/python2.4/Python.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GDESKLETS... configure: error: Package requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GDESKLETS_CFLAGS and GDESKLETS_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for more details.

---

### Post by taurus on 2006-03-03
Are you trying to compile gDesklets?  There is already a binary version in repo so 

```

sudo apt-get install gdesklets

```

---

### Post by armyrebel on 2006-03-03
i dont that computer hooked to the internet,.

---

### Post by taurus on 2006-03-03
You can either download and install gnome-python, pygtk, and pyorbit first before you can build gdesklets from source or you can look around for a .deb version and download it to another machine.  Then, copy it over to Ubuntu and install it with "dpkg -i filename.deb" command.

---

