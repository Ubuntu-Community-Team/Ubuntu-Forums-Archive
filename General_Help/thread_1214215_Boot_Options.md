---
title: "Boot Options"
date: 2009-07-15
forum: General Help
---

### Post by titopagan on 2009-07-15
How can I change the boot options permanently from kernel 2.6.28.13 to kernel 2.6.28.11.

I have searched but I find some of the answers confusing.

I am currently running Ubuntu 9.04.

Thanks for your help.

---

### Post by oldos2er on 2009-07-15
Easiest way is to install the program startupmanager:
```
sudo apt-get update && sudo apt-get install startupmanager
``` Then run
```
gksu startupmanager
```and you can select which kernel you want to boot by default.

---

### Post by egalvan on 2009-07-15
> **oldos2er said:**
> Easiest way is to install the program startupmanager:
```
sudo apt-get update && sudo apt-get install startupmanager
``` Then run
```
gksu startupmanager
```and you can select which kernel you want to boot by default.

+1 for excellent advice... too  often startupmanager is forgotten.

And if you want a "no cli/terminal" way of installing/using  startupmanager... (because "command line is too hard")

use Synaptic

System -> Administration -> Synaptic Package Manager

then do a search for startupmanager...
select it and apply changes.

----

or use Add/Ramove

Applications -> Add/Remove

and search for startup
select it and apply changes...

now see how much easier the command line in a terminal was? :p

-----------------

And you can also launch startup-manager from

System -> Administration

---

### Post by chriskin on 2009-07-15
since we are loving the terminal on this thread, you can always edit the boot options writing sudo gedit /boot/grub/menu.lst and then editing the options on the last part of the file

do that only if you know what you are doing , or feel like reading the instructions it has (or feel clever enough to not mess up)

---

### Post by titopagan on 2009-07-15
> **oldos2er said:**
> Easiest way is to install the program startupmanager:
```
sudo apt-get update && sudo apt-get install startupmanager
``` Then run
```
gksu startupmanager
```and you can select which kernel you want to boot by default.

That worked perfectly.  Thank you so much.

---

