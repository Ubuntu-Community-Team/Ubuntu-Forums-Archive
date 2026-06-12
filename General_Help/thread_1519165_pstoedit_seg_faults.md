---
title: "pstoedit seg faults"
date: 2010-06-27
forum: General Help
---

### Post by Alex Flint on 2010-06-27
Hi there,

I'm having trouble with pstoedit. I'm running Ubuntu 10.04. I'm trying to convert from PDF to SVG, and no matter what PDF I use, pstoedit seg faults:

```
$ pstoedit -f plot-svg square.pdf square.svg
pstoedit: version 3.50 / DLL interface 108 (build Jan 25 2010 - release build - g++ 4.4.3) : Copyright (C) 1993 - 2009 Wolfgang Glunz
Segmentation fault
```

In fact, even running "pstoedit -help" segfaults:
```
$ pstoedit -help
pstoedit: version 3.50 / DLL interface 108 (build Jan 25 2010 - release build - g++ 4.4.3) : Copyright (C) 1993 - 2009 Wolfgang Glunz
[...]
Segmentation fault
```

---

### Post by EricDP on 2010-08-02
Yeah, me too. Odd that there are no other replies - how can we be the only two?

---

### Post by Alex Flint on 2010-08-02
Yeah I never found a solution to this one. Anyone?

---

### Post by trunks14 on 2011-03-31
Compiling my own pstoedit worked for me:

install libplot-dev:
> sudo apt-get install libplot-dev

In your pstoedit directory:
> ./configure --with-libplot --prefix=/usr
> make
> sudo make install

If textext complains about pstoedit not having been compiled with svg support theneEdit textext.py and comment out the following lines:
```

   if 'plot-svg' not in out:
      raise RuntimeError("Pstoedit not compiled with plot-svg support")
```

---

