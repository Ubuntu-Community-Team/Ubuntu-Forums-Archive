---
title: "Development tools"
date: 2006-01-26
forum: General Help
---

### Post by TecSoft on 2006-01-26
Hey everyone. Are there any development tools on Ubuntu like make. I tried makeing ndiswrapper. I did it as root and it said it command does not exist. What should I do?

---

### Post by dickohead on 2006-01-26
Install it.

"sudo apt-get install make"

or if you can't find it:

"sudo apt-cache search make"

---

### Post by TecSoft on 2006-01-26
I dont have internet connection yet. Can I still do it?

---

### Post by dickohead on 2006-01-26
No, because Ubuntu minmizes on things like development to deliver the Ubuntu Distribution on one CD, rather than one DVD or multiple CD's. You will need an Internet connection, or you will need to locate the packages somehow, download them elsewhere and use "dpkg" to install them from CD.

---

### Post by TecSoft on 2006-01-27
Okay I will download it in my WinXp partion and mount it and install it on ubuntu.

---

### Post by psychicdragon on 2006-01-27
build-essential, make, gcc etc. are all on the breezy CD.

```
sudo apt-get install build-essential
``` should be all that's required.

---

