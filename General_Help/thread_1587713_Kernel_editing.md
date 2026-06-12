---
title: "Kernel editing"
date: 2010-10-04
forum: General Help
---

### Post by shashanksingh on 2010-10-04
I want to modify the source code of the kernel so that the new compiled kernel should disable USB ports...

Can anyone please tell me how to go about this????

---

### Post by andrewthomas on 2010-10-04
You don't need to modify the source code.  The changes that you need to make are in the .config.  

Once you make menuconfig, go to Device Drivers > USB support and deselect.

```
CONFIG_USB=n
```

[https://help.ubuntu.com/10.04/installation-guide/amd64/kernel-baking.html](https://help.ubuntu.com/10.04/installation-guide/amd64/kernel-baking.html)

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[http://kernel-handbook.alioth.debian.org/](http://kernel-handbook.alioth.debian.org/)

---

### Post by shashanksingh on 2010-10-04
In the .config file I have many options of CONFIG_USB_*.*
like network adapters, FIR devices, etc.


Could you tell me which is the exact one I would need to say no to if I just want to disable USB drives for that kernel??

Thanks...

---

### Post by _michel_ on 2010-10-04
my 2 cents: if you make xconfig, there is a brief description with each setting  (do ctrl-f to search for USB)
hope it helps

---

### Post by andrewthomas on 2010-10-04
> **shashanksingh said:**
> In the .config file I have many options of CONFIG_USB_*.*
like network adapters, FIR devices, etc.


Could you tell me which is the exact one I would need to say no to if I just want to disable USB drives for that kernel??

Thanks...
If you say no to config_usb there should be no other usb options since they all should depend on config_usb=y

---

