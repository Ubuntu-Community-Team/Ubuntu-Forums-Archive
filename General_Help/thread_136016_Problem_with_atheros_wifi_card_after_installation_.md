---
title: "Problem with atheros wifi card after installation of i686 kernel"
date: 2006-02-25
forum: General Help
---

### Post by Hazzgard on 2006-02-25
Hi everybody,

I'm posting here because I don't get any answer in the french forum. I'm quite a newbie but this is very strange. With the kernel i386 my atheros wifi card works but with the i686 it doesn't. When I do "modprobe ath_pci" I get that this module doesn't exist. "lsmod | grep ath" give me an error. What can I do ?

---

### Post by Jason_25 on 2006-02-25
Do you have the restricted modules for that kernel installed?

---

### Post by Hazzgard on 2006-02-25
Firstable thanks for this quick reply.

I've installed the linux-image-686 installed but no the linux-restricted-modules for that kernel.

Should I install this to get the atheros card work ?

---

### Post by Jason_25 on 2006-02-25
Yes that should provide the madwifi kernel module that is essential for your card to be recognized.

---

### Post by Hazzgard on 2006-02-25
Ok, linux-restricted-modules are installed, but no recognition of my atheros card.

modprobe ath_pci  give an error no modules with this name

What could be the next step ?

---

### Post by Hazzgard on 2006-02-27
Nobody can help me ?

---

### Post by newuser111 on 2006-02-27
try modprobe wlan, ath_hal and ath_pci

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

---

### Post by Hazzgard on 2006-02-27
Everything is ok now. Don't know how but I didn't install the liniux restricted modules fine, I desinstall it and reinstall it and now all is perfect. Strange no ?

Thanks for all everybody ;)

---

