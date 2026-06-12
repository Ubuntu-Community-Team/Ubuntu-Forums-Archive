---
title: "Problem installing Avant Window Navigator"
date: 2010-05-17
forum: General Help
---

### Post by kyletstrand on 2010-05-17
Hello.

I'm trying to install the Avant Window Navigator by compiling the source files and installing that way.  I've extracted the file avant-window-navigator-0.4.0.tar.gz, but when I run the ./configure command, I get an error.

```


configure: error: in `/usr/src/avant-window-navigator-0.4.0':
configure: error: 
  Could not link test program to Python. Maybe the main Python library has been
  installed in some non-standard library path. If so, pass it to configure,
  via the LDFLAGS environment variable.
  Example: ./configure LDFLAGS="-L/usr/non-standard-path/python/lib"
  ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them
```

I have searched around and everything is telling me that my python is up-to-date.

Not sure where to go from here.  Anyone have any ideas?

---

### Post by ajgreeny on 2010-05-17
As the error message says, try installing **python-dev** if you don't already have it.  There may also be other ***python*-dev** packages that are needed, but that's a good place to start.

---

### Post by DOSIX on 2010-05-17
why are you compiling it from source instead of getting it from the software center? it's much easier.

---

### Post by kyletstrand on 2010-05-18
> **ajgreeny said:**
> As the error message says, try installing **python-dev** if you don't already have it.  There may also be other ***python*-dev** packages that are needed, but that's a good place to start.

Nice, thanks.  Totally overlooked that and that's all I needed.

> **DOSIX said:**
> why are you compiling it from source instead of  getting it from the software center? it's much easier.

Just merely for learning purposes.  Although it would be easier to use the software center or Synaptic, I feel like I deserve something when I do a little work to get it working.

---

### Post by realzippy on 2010-05-18
*"There may also be other *python*-dev packages that are needed, but that's a good place to start."*



```
sudo apt-get build-dep avant-window-navigator
```

installs all you need to compile a newer version of awn.

---

