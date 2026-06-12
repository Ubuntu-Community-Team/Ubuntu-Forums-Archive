---
title: "gnome-panel broken!  help!"
date: 2010-11-07
forum: General Help
---

### Post by joshuaos on 2010-11-07
Okay, so on my dad's computer here gnome-panel just spontaneously stopped working.  He says the computer suddenly turned off and then the panels were gone.  When I attempt to start it at the command line (
"gnome-panel"), I get:

gnome-panel: error while loading shared libraries: /usr/lib/libORBitCosNaming-2.so.0: invalid ELF header

I have tried dpkg-reconfigure gnome-panel unsuccessfully.


Any ideas?
THANK YOU!
Joshua

---

### Post by Barriehie on 2010-11-07
Try reinstalling it:
```

# > aptitude reinstall gnome-panel
```

---

### Post by joshuaos on 2010-11-18
No errors are presented when reinstalling gnome-panel, but it still doesn't work, with the same error when I try to start it.

---

### Post by Habitual on 2010-11-18
Try this:

Alt+F2...> gconftool-2 --shutdown

Terminal...> rm -rf ~/.gconf/apps/panel
Terminal...> pkill gnome-panel

---

### Post by WorMzy on 2010-11-18
That file is provided by liborbit2, try reinstalling that package.

```
sudo apt-get install --reinstall liborbit2
```

---

### Post by joshuaos on 2010-12-03
Preparing to replace liborbit2 1:2.14.18-0.1 (using .../liborbit2_1%3a2.14.18-0.1_amd64.deb) ...
Unpacking replacement liborbit2 ...
Setting up liborbit2 (1:2.14.18-0.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libaudiofile.so.0 is not an ELF file - it has the wrong magic bytes at the start.

/sbin/ldconfig.real: /usr/lib/libaudiofile.so.0.0.2 is not an ELF file - it has the wrong magic bytes at the start.

---

### Post by WorMzy on 2010-12-03
That's a strange error. Have you added any third-party repositories to your software sources, or are you just using the standard Ubuntu repositories?

Try fscking your partition (note that this command will restart your system -- save any open documents first)

```
shutdown -rF now
```

If there's any irregularities with your filesystem (which may be causing this problem), this should detect (and hopefully fix) them.

---

