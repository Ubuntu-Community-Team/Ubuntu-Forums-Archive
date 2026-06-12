---
title: "Force apt-get to install with errors"
date: 2010-01-11
forum: General Help
---

### Post by beastrace91 on 2010-01-11
Howdy All,

I have a package on my system that has a missing dependency and I would like to install another piece of software via apt-get with out having to remove my software that is missing a dependency... Can I force it install the other package with out first running **apt-get -f install**?

Thanks,
~Jeff

---

### Post by Leppie on 2010-01-11
you could try downloading the .deb and install with gdebi.

---

### Post by beastrace91 on 2010-01-11
> **Leppie said:**
> you could try downloading the .deb and install with gdebi.

Aside from this - thats why I specifically asked about using apt-get, gdebi just use dpkg - which I can install with regardless.

Thanks,
~Jeff

---

### Post by Leppie on 2010-01-11
> **beastrace91 said:**
> Aside from this - thats why I specifically asked about using apt-get, gdebi just use dpkg - which I can install with regardless.
next time you might want to be a bit clearer in your explanation (like why you do not want to resolve the missing dependencies and why it **has to be** apt-get)if you want such specific help.

---

### Post by slakkie on 2010-01-11
Post the full log, maybe, just maybe we can be helpful enough to fix the dependency issue and then have apt-get install your package like it should :)

---

### Post by beastrace91 on 2010-01-11
> **beastrace91 said:**
> I would like to install another piece of software via **apt-get**

Sorry I thought that was pretty clear :(

Hypothetically speaking - lets say I cannot resolve the issue, can I force apt-get to install a new piece of software or do I have to use dpkg if there is a missing dependency for a package installed?

Thanks,
~Jeff

---

### Post by Leppie on 2010-01-11
i'm not sure, as i never go ahead with missing dependencies.
you could try the "-y" option if you have not tried that yet:
```
sudo apt-get -y install <somepackage>
```

though i think that pre-existing missing dependencies will pretty much prevent you from installing new packages with apt-get.

---

