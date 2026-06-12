---
title: "Adding new headers for g++"
date: 2011-05-12
forum: General Help
---

### Post by phasefirex on 2011-05-12
Hello everyone, I'm not sure if this is the correct forum to ask this, but I need some help installing a new header in g++

I need to use the header "nrutil.h" in my program I just got finished writing. The g++ compiler says it does not exist. I do not know how to add new headers for the g++ compiler to recognize and use.

Could someone help me? Thanks!

---

### Post by TeoBigusGeekus on 2011-05-12
You can put them in /usr/include or you can compile your code with the -I switch, ie.
```
g++ source.cpp -I /path/to/header.h -o myawesomeprogram
```

---

