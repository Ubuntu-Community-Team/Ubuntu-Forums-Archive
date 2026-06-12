---
title: "Sigil not running"
date: 2011-11-05
forum: General Help
---

### Post by donmatas on 2011-11-05
I have Ubuntu 10.04 and I am trying to install Sigil. I downloaded the program from here: [http://code.google.com/p/sigil/downloads/list](http://code.google.com/p/sigil/downloads/list)
then I installed with the following command:

```
chmod +x Sigil-0.4.2-Linux-x86-Setup.bin
sudo ./Sigil-0.4.2-Linux-x86-Setup.bin
```

After instalation I tried to make it run, but nothing happens

```
/opt/sigil$ sigil
No se ha encontrado la orden «sigil», quizás quiso decir:
 La orden «sigit» del paquete «sigit» (universe)
sigil: orden no encontrada
```

```
/opt/sigil$ sh sigil.sh
/opt/sigil/./sigil: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.14' not found (required by /opt/sigil/./sigil)
```

Thanks
DM

---

### Post by donmatas on 2011-11-05
I got an official answer from the [Sigil developers]("http://code.google.com/p/sigil/issues/detail?id=1091"):

```
Comment 1 by project member john@..., Today (5 hours ago)
10.04 is not supported. Sigil requires at least Ubuntu 11.04.

```

It seems that there is nothing to do.

salud 
DM

---

### Post by engine on 2012-05-06
And no chance of downloading an earlier version, I suppose? Pity.

---

