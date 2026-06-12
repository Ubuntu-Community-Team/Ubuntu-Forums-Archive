---
title: "Common practice of installing .tar.gz installs at?"
date: 2010-03-31
forum: General Help
---

### Post by Roasted on 2010-03-31
I've only ever installed two programs that came in .tar.gz's with their own install.sh scripts. Each one recommended to be saved in /opt.

What is opt? Should all .tar.gz programs with their script installer be handled in the opt directory? It's amazing I've used Ubuntu for 4 years and only now thought about it. :P

---

### Post by blueridgedog on 2010-03-31
Some go for /opt.  Some go for /usr/local/bin.  Some go for /home/USER/bin (where USER is your user account).  There are pros and cons to each.  I am a bit "old school" and like /usr/local/bin, but I do keep a /home/USER/bin that is backed up as part of my home directory so that when I restore due to a fresh install I have thos binaries.

If you want some light reading:

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

and if you want some pointless chatter about /usr/local/bin versus /opt:

[http://www.linuxjournal.com/magazine/pointcounterpoint-opt-vs-usrlocal](http://www.linuxjournal.com/magazine/pointcounterpoint-opt-vs-usrlocal)

---

### Post by Roasted on 2010-03-31
What if they recommend /usr/local/bin and I'm like, nah, I don't like /usr/local/bin, and I put it in /opt? Will it work the same way?

---

### Post by john newbuntu on 2010-03-31
bin generally refers to binaries only (Executables).  /opt could have several other sub-directories such as source, libraries etc. So, if you are comfortable with setting links to binaries and LD_LIBRARY_PATHs, then you can install it wherever (with the appropriate permissions of course).  But you could have problems when it comes to upgrades, uninstalls and re-installs.

---

### Post by 3rdalbum on 2010-04-01
> **Roasted said:**
> What if they recommend /usr/local/bin and I'm like, nah, I don't like /usr/local/bin, and I put it in /opt? Will it work the same way?

/opt is not in $PATH. But if you specify the full path it will probably work.

---

### Post by Roasted on 2010-04-01
I installed a game called SecondLife yesterday just as a test-run for helping my cousin out. It installs with an install.sh file, and I placed it in the /opt directory. I was like, ya know, how do I uninstall this thing? Out of curiosity I nuked everything SecondLife related in the /opt folder and sure enough, it wouldn't launch them. I had to remove the icon from the menu, but once that was done I wasn't seeing any trace of it in the system.

Is that the common practice for removing tar.gz installs? Or are there typically a ton of files scattered elsewhere?

---

### Post by blueridgedog on 2010-04-01
> **Roasted said:**
> 
Is that the common practice for removing tar.gz installs? Or are there typically a ton of files scattered elsewhere?

If you manually delete an install location, you may leave some files behind.  This could be user config files in /home/USER, icons in gnome and symbolic links in /bin and other locations.  Some modern applications have uninstall scripts/programs for Linux now, but only if you install in the recommended location.

---

