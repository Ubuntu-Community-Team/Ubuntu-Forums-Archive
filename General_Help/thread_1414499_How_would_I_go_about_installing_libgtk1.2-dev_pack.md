---
title: "How would I go about installing libgtk1.2-dev package in Karmic?"
date: 2010-02-23
forum: General Help
---

### Post by kerryhall on 2010-02-23
I know it exists for Jaunty, but not Karmic. My question is just simply, how can I download this package, and can I just use Synaptic to install it without any problems?

Any detailed documentation about installing "obsolete" packages and their dependencies?

Perhaps is there some way to get my system to emulate Jaunty, I can install the package, then go back to Karmic?

Thanks!

---

### Post by kerryhall on 2010-02-26
Bump.

---

### Post by Sargalus on 2010-02-27
when I tried to install the libgtk1.2-dev package I get this message

Error: Dependency is not satisfiable: libgtk1.2 (= 1.2.10-18)

Im trying to install xmms and I need this package to be able to install it please help

---

### Post by Mark Phelps on 2010-02-27
> **Sargalus said:**
> when I tried to install the libgtk1.2-dev package I get this message

Error: Dependency is not satisfiable: libgtk1.2 (= 1.2.10-18)

Im trying to install xmms and I need this package to be able to install it please help

libgtk1.2 is not the same package as libgtk1.2-dev.

I had to install the same packages to compile another program from source, and you will need the following two packages:
- libgtk1.2 (1.2.10-18.1)
- libgtk1.2-common (1.2.10-18.1)

You can get these using the Debian package search tool at: 

[http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages")

---

### Post by Sargalus on 2010-02-27
I was able to installed libgtk1.2-common, but when I tried to install libgtk1.2 I would get this error message

Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)

I get the same error message for libgtk1.2-dev and libglib1.2-dev

any ideas?

---

### Post by kerryhall on 2010-03-02
> **Mark Phelps said:**
> libgtk1.2 is not the same package as libgtk1.2-dev.

I had to install the same packages to compile another program from source, and you will need the following two packages:
- libgtk1.2 (1.2.10-18.1)
- libgtk1.2-common (1.2.10-18.1)

You can get these using the Debian package search tool at: 

[http://www.debian.org/distrib/packages]("http://www.debian.org/distrib/packages")

Thank you for that link! Will I mess up apt by installing these packages and their deps manually?

---

