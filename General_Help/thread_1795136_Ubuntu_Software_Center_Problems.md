---
title: "Ubuntu Software Center Problems"
date: 2011-07-02
forum: General Help
---

### Post by jsonntag2012 on 2011-07-02
When I first started using Ubuntu 11.04 the Software Center worked fine.  Now whenever i open it up and try to open a category, a window pops up and says  "The report belongs to a package that is not installed".  If I close those windows then i get a little loading animation forever.  If anybody knows how to fix it I will love you forever.

---

### Post by redmaniac on 2011-07-02
Did you install anything recently that might have gone bad, like you connection dropped during download or anything that disrupts the package install? Open  terminal and run 

```
sudo apt-get check
```

---

### Post by knutschr on 2011-07-02
Search for software center in synaptic.
Reinstall the packages.

---

### Post by wildmanne39 on 2011-07-02
> **jsonntag2012 said:**
> When I first started using Ubuntu 11.04 the Software Center worked fine.  Now whenever i open it up and try to open a category, a window pops up and says  "The report belongs to a package that is not installed".  If I close those windows then i get a little loading animation forever.  If anybody knows how to fix it I will love you forever.Hi, is that all the error message says? if there is more post it all here so we can see it.

---

### Post by jsonntag2012 on 2011-07-04
> **redmaniac said:**
> Did you install anything recently that might have gone bad, like you connection dropped during download or anything that disrupts the package install? Open  terminal and run 

```
sudo apt-get check
```


i tried that is says i need to manually run "sudo dpkg --configure -a"

---

### Post by wildmanne39 on 2011-07-05
> **jsonntag2012 said:**
> i tried that is says i need to manually run "sudo dpkg --configure -a"Hi, run these command from the terminal one right after the other finishes.
```
sudo dpkg --configure -a
```
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

