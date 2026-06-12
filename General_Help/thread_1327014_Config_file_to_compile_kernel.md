---
title: "Config file to compile kernel"
date: 2009-11-15
forum: General Help
---

### Post by tapas_mishra on 2009-11-15
I want to know the meanings of the variables in the .config file which is generated via make menuconfig the symbols in it what is the meaning of each and every variable in it ,is it documented any where.

---

### Post by hal10000 on 2009-11-15
If you install the kernel sources and are going to compile a kernel by yourself, then during the configuration you will have he choice to see and read all the informations you are asking for. But it will take a time to browse all the variables (more than 1000 i guess)

---

### Post by MaxIBoy on 2009-11-15
Select the option you wish to know about and hit H for Help. Not all options are documented, but where it exists the documentation is pretty good and includes suggestions for sane defaults ("If you don't know what all that means, you probably need to say No.") That screen will also show what other options any given depends on.

---

### Post by tapas_mishra on 2009-11-16
Ok I got your point but is there any documentation about all those 1000 variables if not then explaining the major portions of the variable say for example I take a look at the device drivers section in that there are a lot of things defined then a broad overview of what those subsections contain if not the exact meanings of variables.

---

### Post by hal10000 on 2009-11-16
> Ok I got your point but is there any documentation about all those 1000 variables
This can also be found in the kernel-source package (in the Documentation folder)

---

### Post by tapas_mishra on 2009-11-16
Ok

---

