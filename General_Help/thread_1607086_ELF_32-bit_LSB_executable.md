---
title: "ELF 32-bit LSB executable"
date: 2010-10-27
forum: General Help
---

### Post by codrgi on 2010-10-27
can someone tell me the packages i need to be able to run a ELF 32-bit LSB executable?

---

### Post by NESFreak on 2010-10-27
You need to make the file executable by ether doing so through its properties dialog or by using the command:
```
chmod +x NAMEOFYOURFILE
```and then you should be able to execute it by typing:
```
./NAMEOFYOURFILE
``` where NAMEOFYOURFILE should obviously be replaced by the actual name your file.

If you're running the 64bit version of ubuntu the 32bit libraries should first be installed. The ia32-libs package should take care of that. Install it either through the synaptic package manager or by running the command:
```
sudo apt-get install ia32-libs
```

---

