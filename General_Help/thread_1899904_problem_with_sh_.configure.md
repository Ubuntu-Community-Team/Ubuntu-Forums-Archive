---
title: "problem with sh ./configure"
date: 2011-12-24
forum: General Help
---

### Post by ubunwhat on 2011-12-24
I am trying to install a more recent version of a program than what is available via Synatpic, but I am running into a few problems.  And I have one question beyond those problems.  This is what I've done so far.

I downloaded the tar.gz2, created a folder in usr/local/ for the program.  Call it app.  So I now have a folder usr/local/app.  Inside the folder I extracted the archive.  I then navigated a terminal to that folder and ran 

```
sudo apt-get build-dep app
```

It downloaded and installed several libraries and I thought I was set.  However, when I ran sh ./configure I encountered the following problem:

```
checking for GLIB - version >= 2.14.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.14.0, but GLIB (2.28.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

Ok, no problem.  I went out and found Glib 2.14.0.  I created a new folder usr/local/glib.  I extracted the archive to that folder.  I ran the sh ./configure for Glib, and it went off without a hitch.  I then ran make install for Glib.  Again, no problems.  It installed successfully.  So no I was ready to rock!  Back I went into usr/local/app, and once again I ran sh ./configure.  And I got....

```
checking for GLIB - version >= 2.14.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.14.0, but GLIB (2.28.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

Yup.  The exact same error.  Now I'm completely confused and more than a bit frustrated.  Any advice on how to get me past this sticking point would be greatly appreciated.

---

### Post by matt_symes on 2011-12-25
Hi

From the terminal try
[FONT=monospace]
[/FONT]```
LD_LIBRARY_PATH="/usr/local/glib" ./configure
```

Kind regards

---

### Post by ubunwhat on 2011-12-25
Just tried.  Same result.  I'm so confused, lol.

---

