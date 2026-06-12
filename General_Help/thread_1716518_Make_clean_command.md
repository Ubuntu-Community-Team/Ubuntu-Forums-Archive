---
title: "Make clean command?"
date: 2011-03-28
forum: General Help
---

### Post by tancrackers on 2011-03-28
When compiling things from source, you generally do cd whatever, .configure, make, sudo make install.
But what about make clean? Should you use it? What is it for? Should I use it for Docky?
Thanks!

---

### Post by doas777 on 2011-03-28
make clean deletes all the already compiled object files. 
if you have a failed make, running make clean before trying again is a good idea.

[http://www.cs.utah.edu/dept/old/texinfo/make/make.html](http://www.cs.utah.edu/dept/old/texinfo/make/make.html)

---

