---
title: "Where do shared-libraries go?"
date: 2009-07-07
forum: General Help
---

### Post by dragos240 on 2009-07-07
Hi, I'm in the /usr directory, and I want to place some shared libraries inside my system, where do shared libraries go, files that end in so.

---

### Post by c0mput3r_n3rD on 2009-07-07
/usr/include ?

---

### Post by ibutho on 2009-07-07
Those shipped by the OS vendor are usually in /usr/lib and those you create yourself should ideally be placed in /usr/local/lib. More info about where things go is available [here]("http://www.pathname.com/fhs/pub/fhs-2.3.html").

---

### Post by dragos240 on 2009-07-07
> **ibutho said:**
> Those shipped by the OS vendor are usually in /usr/lib and those you create yourself should ideally be placed in /usr/local/lib. More info about where things go is available [here]("http://www.pathname.com/fhs/pub/fhs-2.3.html").
Heh..... I just copied my shared objects to /usr/local/lib, but my application will not load, I'm going to try to put them in /usr/lib

---

### Post by ibutho on 2009-07-07
You may need to run "ldconfig" in order for apps to recognise the new libraries.

---

