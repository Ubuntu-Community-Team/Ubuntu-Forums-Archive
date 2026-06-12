---
title: "Empathy sometimes missing menu (i.e. &quot;Chat&quot;, &quot;Edit&quot;, etc.)"
date: 2010-01-07
forum: General Help
---

### Post by nortexoid on 2010-01-07
Sometimes when I start empathy the menu is missing. I've had globalmenu installed but I've removed it and set it so that the menu is showing in the window anyway. But that might still be causing problems--I don't know. Is anyone else witnessing this behavior?

I notice that hen I open programs in a terminal I get the msg:
```
Gtk-Message: Failed to load module "globalmenu-gnome": libglobalmenu-gnome.so: cannot open shared object file: No such file or directory
```

If it were a bug globalmenu caused, I find it odd that the problem has only occurred with Empathy.

---

### Post by falcon1620 on 2010-01-07
I am using Empathy on a regular basis with the 64bit Ubuntu 9.10. I do not notice any odd behaviour like the one you have described. If you run sudo apt-get dist upgrade or any other commands like autoclean or purge do you get any errors with missing dependencies or anything like that? I would go into synaptic package manager from system > administration and check re-install on empathy to see if this helps. Perhaps an upgrade or install did not go well. The Synaptic Package Manager should be able to hep you resolve some of these issues it finds for your computer. Also try installing the missing library... just search for the library name in the package manager... The problem you may discover is that empathy may be a part of a meta package of Gnome, so if you run into issues you could also try removing and re-installing the gnome meta package. If your using network manager, be sure that you will have a network connection outside of GNOME first. I hope you find some of this info helpful.

---

### Post by juvenn on 2010-01-18
I could confirm the issue exactly, and I think it related to global-menu. I guess it may changed some configurations.

---

