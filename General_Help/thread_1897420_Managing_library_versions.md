---
title: "Managing library versions"
date: 2011-12-19
forum: General Help
---

### Post by ofnuts on 2011-12-19
I'm trying to install Gimp 2.7.4 (in /opt). It requires Glib 2.28. My Lucid Lynx uses 2.24

I downloadedI the 2.28 tarball and compiled it (for /usr) and installed it without problems.

Back in the Gimp/Gegl/Babl build, the ./configure step complains that even though I have Glib 2.28, there is still a 2.24 lurking in the path:
```

checking for GLIB - version >= 2.28.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.28.8, but GLIB (2.24.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```I admit I installed 2.28 without really thinking about it. Although I use KDE, I certainly have apps depending on it, even If I can expect them to work with 2.28 if they work with 2.24.

So now the current situation is:

[LIST]
[*]/usr/lib/pkgconfig/glib-2.0.pc says the version is 2.24.1
[*]lib/libglib-2.0.so.0 links to libglib-2.0.so.0.2400.1 (makes me wonder if the make install really worked)
[*]my package manager still sees 2.24 (also wondering if there are things to be done there)
[/LIST]
How do I get out of this mess?

Bonus points: I'm actually trying to use two concurrent versions of Gimp, 2.6 in /usr and 2.7 in /opt. I found how to build Gimp-2.7 for /usr and I thin the same method could be applied to babl/gegl/glib, but will their install procedures automatically pick up the libs in /opt?  

Thx

---

### Post by searchfgold6789 on 2011-12-19
> Bonus points: I'm actually trying to use two concurrent versions of  Gimp, 2.6 in /usr and 2.7 in /opt. I found how to build Gimp-2.7 for  /usr and I thin the same method could be applied to babl/gegl/glib, but  will their install procedures automatically pick up the libs in /opt?  If you compile Gimp from source you will find that they will locate the most-recently installed version of glib, as long as it installed OK.
As for the other issue I'm tempted to tell you to uninstall 2.8 with a good 'make uninstall', uninstall 2.4 and then reinstall 2.8, but that might leave you with a broken system. The best solution for this is to upgrade Ubuntu.

---

