---
title: "How to suspend to RAM?"
date: 2006-02-16
forum: General Help
---

### Post by matts0344 on 2006-02-16
First of all, I have to say, I'm loving Ubuntu, this is really a great operating system. One thing I'm missing though is suspend to RAM. 

In the log out screen it only shows hibernate, but I want my computer to power up directly to the log-in screen. In the power preferences I selected the option to 'suspend' when I press the power button. But all it does is shut down my PC.

Thanks for any help you can give.

---

### Post by agheba on 2006-02-17
open /etc/default/acpi-support with your favorite editor and uncomment the line ACPI_SLEEP=true
It worked with my notebook

---

### Post by StefanoCole on 2006-02-17
Have you already checked in the following wiki? [https://wiki.ubuntu.com/SuspendHowto]("https://wiki.ubuntu.com/SuspendHowto")

Stefano

---

