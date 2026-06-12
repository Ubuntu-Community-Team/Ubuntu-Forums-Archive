---
title: "How is it that transmission is installed and yet not installed?"
date: 2010-04-23
forum: General Help
---

### Post by aviramof on 2010-04-23
when i go to application-internet there is transmission there and it does work it's version 1.92 (10363) but in ubuntu tweak and in synaptic it's not ticked as install and there there is
the same version i think.

---

### Post by SgtPepperKSU on 2010-04-23
Is transmission-gtk installed?  The transmission package is a combination of the GUI (transmission-gtk) and CLI (transmission-cli) versions, but only the GUI version is installed by default.

In the future, you can install dlocate to determine what package installed a given file.

---

### Post by cariboo on 2010-04-23
Transmission-gtk is installed by default, try starting it in a terminal to check for errors.

---

### Post by aviramof on 2010-04-23
i don't understand how can i see errors here when i type transmission it open the software.

---

### Post by SgtPepperKSU on 2010-04-23
> **aviramof said:**
> i don't understand how can i see errors here when i type transmission it open the software.
That's because there are no errors...

---

### Post by aviramof on 2010-04-23
ok so why don't you install transmission-gtk and not transmission as default software?

---

### Post by SgtPepperKSU on 2010-04-23
> **aviramof said:**
> ok so why don't you install transmission-gtk and not transmission as default software?
This is exactly how it is.  The transmission-gtk package is installed by default; the transmission package is not.

What are you asking?

---

### Post by aviramof on 2010-04-23
reversed the names why do install transmission-gtk and not transmission with the cli?

---

### Post by SgtPepperKSU on 2010-04-23
> **aviramof said:**
> reversed the names why do install transmission-gtk and not transmission with the cli?
They decided that most people would use the GUI and not the CLI.  The same reasons for why they do or don't include any package...

---

### Post by aviramof on 2010-04-23
thanks for the information.

---

