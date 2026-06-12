---
title: "Canon iP4600"
date: 2011-09-13
forum: General Help
---

### Post by chinner459 on 2011-09-13
I would be extremely grateful if someone could tell me how to install the driver for my Canon iP4600 printer.  I have downloaded the driver from the Canon website and saved it in a new directory named <Canon> and extracted the deb packages into this directory. From there on in I get nowhere. The system does not appear to be able to find these packages and gives me an error every time I try to <dpkg-deb> with them.  I am using Natty (Naughty?) Narwhal for this excercise.

---

### Post by khelben1979 on 2011-09-13
Did you try ```
sudo dpkg -i [package].deb
``` ?

---

### Post by ajgreeny on 2011-09-13
If there are several .deb files which you need to install but need them in a particular order for it to work, it is probably easiest to put all those .deb files into an empty folder (make one if needed) and then navigate to the folder in terminal and run ```
sudo dpkg -i *.deb
``` This will overcome any problem of the order of install of packages and also each package perhaps being dependent on the other, and therefore impossible to install separately.

---

### Post by khelben1979 on 2011-09-13
I have checked on the .tar file which you've probably downloaded from their webpage, and it consists of 2 .deb files.

I'm wondering if you get any text output on the screen telling you that something went wrong or if you can post any of this it would be helpful to further analyze this problem.

In the attached 2 pictures you can see all the packages which these 2 packages must have in order for you to get a successful installation.

---

### Post by demonipuch on 2011-09-13
Hello

How to install your printer in 3 command lines :
```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-ip4600series
```

---

