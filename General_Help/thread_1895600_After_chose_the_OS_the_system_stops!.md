---
title: "After chose the OS the system stops!"
date: 2011-12-15
forum: General Help
---

### Post by miguelpires on 2011-12-15
Hello!
I'm using Wubi, and after I chose the OS and the system starts to load it stops in Battery cheking! This is a desktop!!
I can enter in rescue mode, but i don't know what to look to fix this!! 
Someone can please help?
Regard's
Miguel

---

### Post by miguelpires on 2011-12-15
I've re-intall the x-server and the lgthm and i can't enter with the normal secion, only in rescue mode. 
Please help!

---

### Post by BC59 on 2011-12-15
From the boot screen, select the normal boot and press **e**. This let's you edit some options in another screen. Select the line that starts with **kernel** and press **e** again. 

Add the option **acpi=off** at the end of the line and press **b** to continue booting. 

If you like to permanently add this option, edit /boot/grub/menu.lst

---

### Post by miguelpires on 2011-12-15
> **BC59 said:**
> From the boot screen, select the normal boot and press **e**. This let's you edit some options in another screen. Select the line that starts with **kernel** and press **e** again. 

Add the option **acpi=off** at the end of the line and press **b** to continue booting. 

If you like to permanently add this option, edit /boot/grub/menu.lst

Hi,
tk for this. I found my problem, something related to numlookx. I've to re-install the thing, and, for now, everything is ok.
Thks Again for your time!

---

