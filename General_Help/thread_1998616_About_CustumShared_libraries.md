---
title: "About Custum/Shared libraries"
date: 2012-06-07
forum: General Help
---

### Post by madhu542 on 2012-06-07
Hi,

I have few questions (below) to ask about custom/Shared libraries, please anybody clarify me.

a.      Under Linux, what are the common locations where custom libraries are installed?

b.      If the libfoo library is not installed in a standard path, how do you specify the correct path to the linker for the library?


c.      If libfoo is a shared library, how does the loader find it at runtime, since it is not installed under a standard path? Is there more than one way to solve this?


d.      When your application links to libfoo, the library is specified as libfoo.so.2.4.0. What do the numbers signify?

e.      If instead, the linker command for your application specifies the library as libfoo.so.2, but the actual library file is libfoo.2.5.2. Will this cause a problem?

---

### Post by madhu542 on 2012-06-07
> **madhu542 said:**
> Hi,

I have few questions (below) to ask about custom/Shared libraries, please anybody clarify me.

a.      Under Linux, what are the common locations where custom libraries are installed?

b.      If the libfoo library is not installed in a standard path, how do you specify the correct path to the linker for the library?


c.      If libfoo is a shared library, how does the loader find it at runtime, since it is not installed under a standard path? Is there more than one way to solve this?


d.      When your application links to libfoo, the library is specified as libfoo.so.2.4.0. What do the numbers signify?

e.      If instead, the linker command for your application specifies the library as libfoo.so.2, but the actual library file is libfoo.2.5.2. Will this cause a problem?

libfoo is just for an example (custom vender supplied binary directory)

---

