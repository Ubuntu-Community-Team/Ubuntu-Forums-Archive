---
title: "Installing an application as root"
date: 2010-06-25
forum: General Help
---

### Post by alan_uk on 2010-06-25
I am trying to install trueimagelinuxserver8.  I have unpacked the tar.gz and: 
aldean@aldean-desktop:~$ cd true*
aldean@aldean-desktop:~/trueimagelinuxserver8.0-914.s.e$ 

I then did 

./trueimage-setup

and got a blue splash screen 

trueimage-setup must be run as root

My question is how can I run it as root if root has been disabled in Ubuntu?

thank you

Alan

---

### Post by philinux on 2010-06-25
As long as it's from a reliable source.

```
sudo ./trueimage-setup
```

---

### Post by alan_uk on 2010-06-25
Many thanks for that.  Useful for all future installs

Alan

---

### Post by philinux on 2010-06-25
> **alan_uk said:**
> Many thanks for that.  Useful for all future installs

Alan

Be sure not to use sudo when there is no need.

---

