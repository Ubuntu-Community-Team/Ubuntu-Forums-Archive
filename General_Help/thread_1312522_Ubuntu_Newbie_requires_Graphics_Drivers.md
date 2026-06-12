---
title: "Ubuntu Newbie requires Graphics Drivers"
date: 2009-11-03
forum: General Help
---

### Post by DubiousHedgehog on 2009-11-03
Hello all.

I'm a complete Ubuntu newbie. (Everyone has to start somewhere.)

I have issues with my Graphics card.
It is a Zotac GTX260, (Nvidia stable) anyway went to the website and downloaded the relevant driver, however Ubuntu is saying it doesn't recognise BIN files.

Any ideas?

Oh I'm running Ubuntu Studio v8.04

And any plug-ins for converting windows files would be appreciated. 

Thanks in advance.

---

### Post by zvacet on 2009-11-03
Applications>accessories>terminal and if you downloaded file on desktop type
```
cd Desktop
```

if you downloaded file in home directory type


```
sudo chmod +x package_name.bin
```

```
sudo ./package_name.bin
```

package_name = real name of your package (driver)

---

### Post by DubiousHedgehog on 2009-11-04
Hmm Tried that, Tells me I'm running an X server whatever that is....

---

