---
title: "c compiler"
date: 2006-05-05
forum: General Help
---

### Post by ivansv on 2006-05-05
when ./configure on a pkg i am getting "c compiler cannot create executables" as an error. i have gcc, make, etc. installed, what pkg or pkgs am i missing here?? or is it merely the cmd arg., etc. appreciate any words of wisdom, thanks.

---

### Post by ekarni on 2006-05-05
Do you have the "build-essential" package?  It's always the first place to start when something won't compile.  

I assume you've found the command line already, so just type
```

sudo apt-get install build-essential

```
there or get the package with Synaptic (graphical package management program).

---

