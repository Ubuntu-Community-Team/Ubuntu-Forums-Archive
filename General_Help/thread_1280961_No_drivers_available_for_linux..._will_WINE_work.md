---
title: "No drivers available for linux... will WINE work?"
date: 2009-10-02
forum: General Help
---

### Post by Stamets2 on 2009-10-02
hello, my laptop manufacturer does not make drivers for anything but windows.. does it work to install drivers via WINE ?



thanks..

- Stamets2

---

### Post by meijer.o on 2009-10-02
No,

This will not work as wine cannot control your hardware directly. You can use wine to install (some) windows programs in a linux environment. ndiswrapper is the only "wrapper" you can use. It is mend, and works for many wireless drivers.

---

### Post by bwang on 2009-10-02
Have you tried the LiveCD yet? Ubuntu has lots of drivers built in. You should be able to make your wireless work using ndiswrapper.

---

### Post by chriskin on 2009-10-02
> **Stamets2 said:**
> hello, my laptop manufacturer does not make drivers for anything but windows.. does it work to install drivers via WINE ?



thanks..

- Stamets2

you don't need the manufacturer's drivers, there are plenty others out there doing just as good , or even better, work

most probably , you won't even need to install them , as most (other than graphics cards that need installing from system/admin/hardware drivers) will work out of the box - for the hardware that doesn't, there is always some tutorial :)

---

### Post by Stamets2 on 2009-10-02
thanks for the responses..


although what I wanted to hear is "ya man, should work fine" I still appreciate the help

great community

-- Stamets

---

### Post by Chronon on 2009-10-02
Get a LiveCD and give it a spin.  This will give you the best idea (other than possibly graphics) of what you can expect as far as hardware support.  As others have said, a lot of hardware is supported in the kernel already and for most hardware there's no installation of 3rd party drivers necessary.

---

### Post by XCan on 2009-10-03
Which parts of the hardware are you concerned about? Even though your laptop manufacturer doesn't provide drivers, it doesn't mean that the hardware manufactureres don't. For example, in Windows my HP laptop has terribly old drivers for the graphics chip, and the network card. But a whirl at nvidia and Intel fixes that. :p

---

