---
title: "Changing the class path...I think (obvious newbie here)"
date: 2010-12-01
forum: General Help
---

### Post by Chrismont on 2010-12-01
Hi Ubuntu forums, I'm a linux newbie who just switched over to the newest release of Ubuntu (10.10), I believe. I'm also new to the forums, so if this thread is on the wrong boards,I apologize.  I've managed to get pretty far by googling and testing, to the point where I've been able to extract, compile and install programs, however i recently attempted to compile a GUI and it gave me the following error message: 
[COLOR="Green"]checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
[/COLOR]
I downloaded the package needed "gtk+-2.0", but I don't know how to incorporate this package into the GUI program. I was told by a friend that I needed to change the class path, I think? Any help on the matter would be greatly appreciated, thank you.

---

### Post by sisco311 on 2010-12-01
Welcome to the forums!

I think you have to install libgtk2.0-dev:
```
sudo apt-get install libgtk2.0-dev
```

---

### Post by Chrismont on 2010-12-03
Thanks so much for the help, sisco:D

---

### Post by sisco311 on 2010-12-03
> **Chrismont said:**
> Thanks so much for the help, sisco:D

My pleasure.

---

