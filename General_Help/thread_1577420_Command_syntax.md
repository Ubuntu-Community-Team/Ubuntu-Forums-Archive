---
title: "Command syntax"
date: 2010-09-18
forum: General Help
---

### Post by Captain Giraffe on 2010-09-18
How does this line work?
```

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

As seen in a thread about webcams for flash and skype.

---

### Post by cgroza on 2010-09-18
You have to run that into a terminal.

---

### Post by Captain Giraffe on 2010-09-18
Yes but how does it work.  Is LD_PRELOAD something that every application recognizes?

---

### Post by Captain Giraffe on 2010-09-22
Bump?!

---

### Post by sisco311 on 2010-09-22
LD_PRELOAD is an [environment variable]("http://en.wikipedia.org/wiki/Environment_variable") which is passed to skype's environment.

Check out:
[uhelp]community/EnvironmentVariables[/uhelp]
[http://www.lostwebsite.net/2010/01/ld_preload-fun/](http://www.lostwebsite.net/2010/01/ld_preload-fun/)
and
[http://en.wikipedia.org/wiki/Dynamic_linker](http://en.wikipedia.org/wiki/Dynamic_linker)

---

### Post by pbrane on 2010-09-22
I don't think LD_PRELOAD is used by the application, it's the runtime linker that reads that environment variable and preloads the requested library.

The command line the OP posted sets the environment variable LD_PRELOAD to point to the shared library */usr/lib32/libv4l/v4l1compat.so* and then runs skype. You could do the same thing by typing the LD_PRELOAD line hitting enter and then typing skype and hitting enter.

---

