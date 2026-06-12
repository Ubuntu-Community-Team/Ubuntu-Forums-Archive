---
title: "How to compile the new hdparm? Plz help .."
date: 2010-04-19
forum: General Help
---

### Post by latebeat on 2010-04-19
Hello all...

I've been using ubuntu for the past year now but unfortunately I have to confess I never had to compile anything from scratch. 
I bought a new intel SSD drive and I've been running some benchmarks on it with various fs. The new hdparm version has a few features that I'd like to test (TRIM/wiper) but I don't know how to install it as it's not in the repositories. I've been googling for almost 4hrs now but I still haven't found a way to do it. 
I've downloaded the tar.gz file from sourceforge and I've decompressed it. Inside, it was a debian folder but there was no .deb file in it. Anyway I did a "make hdparm" and it compiled with no errors. It gave me an "hdparm" executable which works fine if I call it with the full path. 
*However, my question is what's the proper way to install it in place of the already apt-get installed package?*

Any help is greatly appreciated as I've reached a dead end :(

thanks

---

### Post by nexes128 on 2010-04-19
From the hdparm folder (i.e. the spot where you did "make hdparm") try 
```
sudo make install
```

---

### Post by latebeat on 2010-04-19
> **nexes128 said:**
> From the hdparm folder (i.e. the spot where you did "make hdparm") try 
```
sudo make install
```

wow...
it was that simple.. :-)
thank u

---

