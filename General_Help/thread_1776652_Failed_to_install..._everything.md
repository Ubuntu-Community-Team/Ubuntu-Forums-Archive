---
title: "Failed to install... everything"
date: 2011-06-06
forum: General Help
---

### Post by Jbakies on 2011-06-06
everytime I install anything I get this error message it happens with everything I install: 
Errors were encountered while processing: 
 firmware-b43-installer 
Setting up firmware-b43-installer (4.150.10.5-5) ... 
Not supported low-power chip with PCI id 14e4:4315! 
Aborting. 
dpkg: error processing firmware-b43-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1

Thanks for the help

---

### Post by wolfen69 on 2011-06-06
Try
```
sudo dpkg --configure -a
```

---

### Post by Jbakies on 2011-06-06
Same thing....

---

### Post by Jbakies on 2011-06-06
I just realized that everything works after I install it even with the error.... still want to fix it

---

### Post by MabelC on 2012-02-10
I also get an error, not supported low power chip... 

DOES ANYONE KNOW HOW TO STOP THIS, IT WONT LET ME INSTALL ANYTHING?!

---

