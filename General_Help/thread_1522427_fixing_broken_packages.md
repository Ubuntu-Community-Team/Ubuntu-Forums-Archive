---
title: "fixing broken packages"
date: 2010-07-02
forum: General Help
---

### Post by Oolongtea on 2010-07-02
I'm trying to do this:


```
deb http://archive.canonical.com/ lucid partner]
```

Then update:
```
sudo apt-get update
```
Then this:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

The last code when entered says I have a broken package that needs to be fixed. The terminal tells me to enter the code below to fix the broken package but nothing changes. I still have a broken package. Any help would be greatly appreciated.

```
sudo apt-get -f install
```

---

### Post by philinux on 2010-07-02
Can you post back any errors from this.

```
sudo dpkg --configure -a
```
To enable the partner repo is as simple as this. System>admin>software sources>other software Tab and tick partner.

---

### Post by Oolongtea on 2010-07-02
Now software sources and synaptic package manager are informing me of this:


E: The package sun-java6-jre needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I can't open anything!!!!HELP!

---

### Post by philinux on 2010-07-02
> **Oolongtea said:**
> Now software sources and synaptic package manager are informing me of this:


E: The package sun-java6-jre needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Similar so substitute your package. See post 18 and 19.
[http://ubuntuforums.org/showthread.php?p=9517069#post9517069](http://ubuntuforums.org/showthread.php?p=9517069#post9517069)

---

### Post by Oolongtea on 2010-07-02
Thanks :)

---

