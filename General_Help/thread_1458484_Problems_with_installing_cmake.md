---
title: "Problems with installing cmake"
date: 2010-04-20
forum: General Help
---

### Post by JCBARCA on 2010-04-20
Hi. I need to install cmake on Ubuntu, but cmake only gives me the following error:

Error when bootstrapping CMake:
Cannot find appropriate C++ compiler on this system.
Please specify one using environment variable CXX.
See cmake_bootstrap.log for compilers attempted.

I have tried to install several C++ compilers but it does not seem to work :(.

Can some one please tell me what I can do to solve the problem:confused:

---

### Post by zvacet on 2010-04-20
Do you have build-essential installed?If you don't type in terminal

```
sudo apt-get install build-essential
```

after that try to install cmake again.

---

### Post by gmargo on 2010-04-20
No need to build it; just install the **cmake** package.  It's in the main repository.

[http://packages.ubuntu.com/karmic/cmake](http://packages.ubuntu.com/karmic/cmake)

---

