---
title: "downgraded to Compiz 8.6 &amp; Classic Ubuntu: Problems with upgrading"
date: 2011-07-15
forum: General Help
---

### Post by ba0bab on 2011-07-15
Hi, 

I downgraded to Compiz 8.6 with the GNOME 2 desktop using these instructions:

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

Today, however, my system wanted to do a "system upgrade", and now I get warning messages like this:


```
emil@Emilubuntu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on unity; however:
  Package unity is not installed.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-desktop
```

and when trying update manager:

Software index is broken

```
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first
```

Now I'm not sure it is good advice to do sudo apt-get install in force mode, since the problem seems to be - I'm guessing - that update manager is trying to install packages with are for the unity desktop and not my classic gnome+compiz 8.6 desktop.

I don't want to ruin anything... can you guys help? Thanks!

- Emile

---

### Post by andrewthomas on 2011-07-15
ubuntu-desktop is a meta-package that depends on unity.

If you do not want to have unity installed, then run

```
sudo dpkg -r ubuntu-desktop
```

in the terminal.

---

### Post by ba0bab on 2011-07-17
Thanks, that did the trick! 

For some reason I had to reinstall my ATI-driver as well, since it got disabled in the process. Go figure

---

