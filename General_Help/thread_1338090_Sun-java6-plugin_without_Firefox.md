---
title: "Sun-java6-plugin without Firefox"
date: 2009-11-26
forum: General Help
---

### Post by joehc on 2009-11-26
Hello
I'm sort of new to ubuntu.
I'm using chrome in ubuntu 9.10, and i'm trying to get java to work with chrome. So figure I need sun-java6-plugin. But every time I try to install it, it also installs firefox. And when I'm trying to uninstall Firefox it also uninstalls sun-java6-plugin. Is it possible to ONLY just install sun-java6-plugin?

Hope you guys can help me

/joe

---

### Post by Brandon Williams on 2009-11-26
The sun-java6-plugin package is dependent upon one of a list of browsers, but chrome is not on the list. The only way to make it work without installing another browser would be to modify the package in order to add chrome to the list of browsers or remove the browser dependency altogether.

I don't recommend this, because it could cause trouble if/when sun-java6-plugin has updates due to the fact that the new version will re-enstate the old, bad dependency. You're better off just installing the most lightweight browser that satisfies the dependency. For example, you could get away with just installing xulrunner, instead of installing all of firefox.

---

### Post by Brandon Williams on 2009-11-26
If you want to modify the package dependencies for sun-java6-plugin (I still recommend against it), here's how to do it. This example assumes that the filename of the downloaded .deb file is sun-java6-plugin_6-15-1_i386.deb. If the architecture or the version number is different, you'll have to change them throughout the list of commands.
```
$ aptitude download sun-java6-plugin
$ mkdir -p sun-java6-plugin_6-15-1_i386/DEBIAN
$ chmod 755 sun-java6-plugin_6-15-1_i386/DEBIAN
$ dpkg -x sun-java6-plugin_6-15-1_i386.deb sun-java6-plugin_6-15-1_i386
$ dpkg -e sun-java6-plugin_6-15-1_i386.deb sun-java6-plugin_6-15-1_i386/DEBIAN/
$ nano sun-java6-plugin_6-15-1_i386/DEBIAN/control
  ... edit control file as described below ... 
$ dpkg --build sun-java6-plugin_6-15-1_i386
$ dpkg -i sun-java6-plugin_6-15-1_i386.deb
```

When you edit the control file, look for the line that starts with 'Depends: '. You'll notice that at the end of the line, there is a list of browser names separated by '|' symbols. Delete that whole list of browser names and be sure not to leave a dangling comma on the end of the line.

---

