---
title: "Ubutu COMPLETELY offline!"
date: 2009-12-02
forum: General Help
---

### Post by Triphido on 2009-12-02
I've no Internet conection at home so i have to download packages running a download script in other pc.  I found a problem installing manually .deb's (yes, i know it's dangerous but i haven't alternative). Package *abiword *for example depends on *abiword-commons,* which isn't installed,so it rejects to be installed. But  *abiword-commons *depends on* abiword*. I can't  install one without the other.

I think that solution could be use the command *dpkg --force-depends* or *dpkg --ignore-depends* but it seems dangerous.

¿Any other idea? ¿have I to assume the risk of using this commands? Thaks...and sorry, my English is very poor!

---

### Post by zvacet on 2009-12-02
Solution is to install both packages at the same time.Let say you downloaded them in your home directory.Applications>accessories>terminal and type

```
sudo dpkg -i abiword abiword-commons
```

You can also try [Keryx]("http://keryxproject.org/")

---

### Post by alien8tive on 2009-12-02
> **zvacet said:**
> Solution is to install both packages at the same time.Let say you downloaded them in your home directory.Applications>accessories>terminal and type

```
sudo dpkg -i abiword abiword-commons
```

You can also try [Keryx]("http://keryxproject.org/")


The best option (however, not advised) is to ignore the dependencies.

Not sure the program will work though.

---

### Post by Cheesemill on 2009-12-02
+1 for Keryx

---

### Post by wojox on 2009-12-02
I like [APTonCD]("http://aptoncd.sourceforge.net/")

---

### Post by 3rdalbum on 2009-12-02
> **zvacet said:**
> Solution is to install both packages at the same time.Let say you downloaded them in your home directory.Applications>accessories>terminal and type

```
sudo dpkg -i abiword abiword-commons
```

+1 (except that you need to give the full name of the debs, I think).

---

### Post by EXCiD3 on 2009-12-02
Don't use dpkg if you can help it. It can easily break things forcing it.

Instead, copy the files into /var/cache/apt/archives. Then run the aptitude or synaptic install on abiword. This will use the packages from the cache and install them as if aptitude/synaptic had downloaded them for you. Works like a charm every time and will never break anything. Just got to make sure you have all the packages and versions. [Keryx]("http://keryxproject.org") can help you get those.

---

