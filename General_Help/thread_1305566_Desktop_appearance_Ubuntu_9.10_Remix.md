---
title: "Desktop appearance Ubuntu 9.10 Remix"
date: 2009-10-30
forum: General Help
---

### Post by Serror on 2009-10-30
I have installed Ubuntu 9.10 Remix beta. I had it for 3 months already and got some experience with Linux. Generally I can manage simple staff. Two days ago I I upgraded my system to final 9.10 Remix and I cant switch  my desktop to a classical view.  In Beta version there was an icon in the system folder with this function, witch not longer exist in the final version. I try to install some scripts for Ubuntu 9.04. Dint work. Any suggestions. Please help...

:(

---

### Post by FrostCake on 2009-10-30
Same here. Desktop-switcher was not installed on my the 9.10nix after the upgrade.

Installing desktop-switcher 0.5.8 fixed it.
[https://launchpad.net/desktop-switcher](https://launchpad.net/desktop-switcher)

---

### Post by Serror on 2009-10-30
Couldn't do it. This fix did not install, 

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  gconf-2.0
                  gmodule-2.0
                  gio-2.0
                  ) were not met:

No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by FrostCake on 2009-10-30
Install 

sudo apt-get install libgtk2.0-dev libgconf2-dev

---

### Post by moonworks on 2009-11-10
there is a workaround to get rid off these nasty huge buttons by deleting the netbook-launcher: [http://ubuntuforums.org/showthread.php?p=8284816](http://ubuntuforums.org/showthread.php?p=8284816)

worked for what i had in mind, but i do not know if this is exactly what you were planning to achieve...

---

