---
title: "Python version conflict"
date: 2011-05-27
forum: General Help
---

### Post by hiKen on 2011-05-27
Hi

I've installed EPD, and it comes with its own Python interpreter. In order to make it the default python interpreter in Ubuntu, instead of the one in /usr/bin, i've renamed the one existing there and created a simlink to the folder where I have EPD installed. Like this:

```

joao@joao-laptop:/usr/bin$ ls -la python*
lrwxrwxrwx 1 root root    9 2011-05-27 20:19 python -> python2.7
lrwxrwxrwx 1 root root   34 2011-05-27 20:15 python2.7 -> /usr/local/epd-7.0.2/bin/python2.7
lrwxrwxrwx 1 root root   41 2011-05-27 20:15 python2.7-config -> /usr/local/epd-7.0.2/bin/python2.7-config

```

and it seems to work as it sees EPD as the default Python:

```

joao@joao-laptop:/usr/bin$ python --version
Python 2.7.1 -- EPD 7.0-2 (32-bit)

```

However, there is something wrong with my system, since there's a red sign in the notification area saying "a problem ocurred while checking for updates", Empathy says there's a "Network error" (which is strange since firefox works perfectly), and when I try to run Compiz Settings Manager trough the terminal (nothing happens when I try trough the menus), it gives the following error:

```

joao@joao-laptop:/usr/bin$ sudo ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 30, in <module>
    import pygtk
ImportError: No module named pygtk

```

I think all of this is pretty strange, but I've gone as far as my knowledge let me, I really dont know what to do now...

I've noticed that the bin folder on the EPD directory also has some other files that match some on the /usr/bin, I dont know if making the link to the EPD folder would work, since none of them is the "pygtk" module.


Help Please!

Thanks in advance!

....

---

### Post by katykat on 2011-05-27
Do yourself a favor and try to symlink to the stystem Python, instrad of the other way around. 

In Jaunty I went through a nightmare trying to modify versions of Python and Perl. Never again. I moved my developmental and cutting edge apps over to Fedora where there arent so many freaking things *HARDWIRED *into the system. 

Meerkat seems pretty stable, but I dont mess with its innards, and Natty has the Unity chain around its neck. 

I Ubuntu I also made the mistake of downloading Python 3.0.


Never again....

---

### Post by hiKen on 2011-05-28
> **katykat said:**
> Do yourself a favor and try to symlink to the stystem Python, instrad of the other way around. 

In Jaunty I went through a nightmare trying to modify versions of Python and Perl. Never again. I moved my developmental and cutting edge apps over to Fedora where there arent so many freaking things *HARDWIRED *into the system. 

Meerkat seems pretty stable, but I dont mess with its innards, and Natty has the Unity chain around its neck. 

I Ubuntu I also made the mistake of downloading Python 3.0.


Never again....

Well, it really seems to be a hassle to make this work, but I'm interested in using some EPD modules, like pybrain and mahotas.

I'm using Natty with Gnome 2, so I dont think Unity will cause any problems.

---

