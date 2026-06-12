---
title: "linux-ubuntu-modules-$(uname -r) not found:"
date: 2009-10-06
forum: General Help
---

### Post by markp1989 on 2009-10-06
im followin this guide .[http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230)

apt cannot find linux-ubuntu-modules-$(uname -r)  

i then tried to install the other packages that apt could find.

which trigers an initramfs update, which is failing . 

now i cannon remove the packages, i get told to 

sudo dpkg --configure -a which tries to make the initramfs which fails again.

now this has happened i cannot install or remove anything using apt.

and i dont want to reboot because i dont know what state this has left the initramfs in.

thanks for any help:

markp1989

edit i removed the installed packages with dpkg.

to continue i need to no the new name of the linux-ubuntu-modules?

thanks markp1989

---

