---
title: "Unable to install wvdial package from .deb file on Ubuntu 12.04"
date: 2012-08-02
forum: General Help
---

### Post by amadeuslin on 2012-08-02
Hi,

I use Ubuntu 12.04 on a HP pavilion-dv6-6050 laptop. I tried to install wvdial packaage from the .deb file. While I installed the other per-requisite packages(viz. wvstreams, libconf etc.), I am unable to install the package using the .deb file via the software centre.

I am unable to click on the install icon and the software centre shows a message " Install wvdial from a trusted source".

Can you help me to proceed and install wvdial from the package?

---

### Post by drmrgd on 2012-08-02
That package is located in the repository.  You shouldn't have to manually install it and its dependencies.  Did you search the Software center for that package?  If it's not showing up, you can get into the terminal and run:

```
sudo apt-get install wvdial
```

---

### Post by Kundan Negi on 2012-08-02
first type this in Terminal
 sudo apt-get install wvdial
If it shows that some pre-requisites are needed,then type
  sudo apt-get install -f
and the previous command.Hope it will work for you:P

---

