---
title: "newbie needs help fixing damaged package from Gimp install"
date: 2011-11-02
forum: General Help
---

### Post by Red Razor on 2011-11-02
Tried to install Gimp using Ubuntu 11.10 Software Center. Something went wrong and I keep getting "Items cannot be installed or removed until the package catalog is repaired". Tried to just click the repair button but problem not solved. Cannot install any software without getting this message now. 

Also tried going to the terminal and entering "sudo at-get -f install" but that didn't work either. Here is the error code I get when I enter the command above. 
```
Preparing to replace gimp 2.6.11-2ubuntu4 (using .../gimp_2.7.4-2011102201~oo_i386.deb) ...
Unpacking replacement gimp ...
dpkg: error processing /var/cache/apt/archives/gimp_2.7.4-2011102201~oo_i386.deb (--unpack):
 trying to overwrite '/usr/lib/gimp/2.0/plug-ins/file-xmc', which is also in package gimp-plugin-registry 3.5.4-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.7.4-2011102201~oo_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help would be greatly appreciated.

---

### Post by duke.tim on 2011-11-09
```
sudo apt-get -f install
```


Using google I found this
sounds like you may need to manually repair the issue

[http://hostechs.com/tag/usrbindpkg-returned-an-error-code-1/](http://hostechs.com/tag/usrbindpkg-returned-an-error-code-1/)

except it would be /var/lib/dpkg/info/gimp

---

