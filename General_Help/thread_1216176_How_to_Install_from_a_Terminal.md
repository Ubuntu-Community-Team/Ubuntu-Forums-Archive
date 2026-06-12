---
title: "How to Install from a Terminal"
date: 2009-07-18
forum: General Help
---

### Post by jerrardm09 on 2009-07-18
I need some serious help on how to install from a terminal window. I am trying to install VMWare tools, but have no clue how to do it. If someone could help me out with the commands would be nice!

---

### Post by ptsubin on 2009-07-18
Have you downloaded the packages? What format are they in? If you want to install from the repositories,
you can type sudo apt-get install <package name>
to reload the repositories, sudo apt-get update.

---

### Post by vinutux on 2009-07-18
if you have installer of vmware with you...

is the installer in .deb format ```
sudo dpkg -i /[COLOR="Red"]pathtoyourinstaller[/COLOR]
```

is the installer in rpm or tar.gz you want to convert it to deb using a tool called alien.

the installer is .run extension...just run it from terminal

.

---

