---
title: "openjdk"
date: 2010-09-25
forum: General Help
---

### Post by walwal on 2010-09-25
i installed both java and openjdk runtimes on my ubuntu lucid.
now when i try to remove openjdk it says that all my installed java applications will be removed with it :s
what can i do?

---

### Post by philinux on 2010-09-25
> **walwal said:**
> i installed both java and openjdk runtimes on my ubuntu lucid.
now when i try to remove openjdk it says that all my installed java applications will be removed with it :s
what can i do?

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Out of date but only bit thats wrong is that you need to enable the Partner repo in Sys>admin>software sources.

---

### Post by walwal on 2010-09-28
that didnt help me much.

---

### Post by gandaran on 2010-09-28
> **walwal said:**
> i installed both java and openjdk runtimes on my ubuntu lucid.
now when i try to remove openjdk it says that all my installed java applications will be removed with it :s
what can i do?
if you have any application that depends on openjdk then you will have to keep openjdk installed!
what you can do is just remove the icedtea-plugin only and keep or install the sun-java6-plugin so firefox will be using sun-java and not open-java.

---

