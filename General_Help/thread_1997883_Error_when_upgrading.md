---
title: "Error when upgrading"
date: 2012-06-05
forum: General Help
---

### Post by TimEnid on 2012-06-05
After doing sudo apt-get upgrade, i get the following error


```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
 any ideas?

---

### Post by TimEnid on 2012-06-10
anyone?

---

### Post by ExSuSEusr on 2012-06-10
Upgrading is very much hit or miss.  I would recommend backing everything up and just doing a clean install.


Of all the times I have ever tried to upgrade - I ended up have to fresh install anyway because of all the problems.

---

### Post by HarryTorry on 2012-06-10
Try doing the following, to force an install of the files that didn't get loaded because of the error;
```
sudo apt-get -f install
``` 

Then try apt-get upgrade again, apt-get -f install back and forth until only the package that has the error is left.

I'd also suggest going with ExSuSEusr and backing your files up first!

---

### Post by TimEnid on 2012-06-12
a clean install? this would be my second time doing that since installing 12.04. if i must.

---

