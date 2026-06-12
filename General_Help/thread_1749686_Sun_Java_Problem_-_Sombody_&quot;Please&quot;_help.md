---
title: "Sun Java Problem - Sombody &quot;Please&quot; help? Thanks,"
date: 2011-05-04
forum: General Help
---

### Post by Keypel on 2011-05-04
I have sun-java6.bin, sun-java6.jre, and sun-java6.plugin installed however here is the output of $ java -version

```
Keypel@Ubuntu:~$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.7) (6b20-1.9.7-0ubuntu1~10.04.1)
OpenJDK Client VM (build 19.0-b09, mixed mode, sharing)
Keypel@Ubuntu:~$ 

```

---

### Post by peyre on 2011-05-04
Why the scare quotes?  Do you not really mean to ask politely? :o

It looks like Java versions are deceptively labeled.  Version 6 reports as version 1.6.  See below.

[http://javatester.org/version.html]("http://javatester.org/version.html")

---

### Post by 4Orbs on 2011-05-04
To change java:
```
sudo update-alternatives --config java
```

---

### Post by Keypel on 2011-05-04
> **peyre said:**
> Why the scare quotes?  Do you not really mean to ask politely? :o

no, actually I was trying to ask politely. Sorry if that somehow came out wrong.

---

### Post by Keypel on 2011-05-04
> **4Orbs said:**
> To change java:
```
sudo update-alternatives --config java
```

Thank You, that worked!

---

### Post by 4Orbs on 2011-05-04
Great. I found it in the Ubuntu Wiki, and FWIW your thread title seems polite and appropriate.

---

### Post by peyre on 2011-05-04
> **Keypel said:**
> no, actually I was trying to ask politely. Sorry if that somehow came out wrong.

No, I didn't think you were being rude.  I was just giving you a hard time for using quotes when you weren't quoting someone or implying that someone was using the word insincerely.

Looks like I'm the one who missed the mark on this one, on a couple of points. :oops:

---

