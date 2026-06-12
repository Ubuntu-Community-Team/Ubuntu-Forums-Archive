---
title: "Making Windows 7 default OS in Grub"
date: 2010-05-11
forum: General Help
---

### Post by Cityscape on 2010-05-11
I have Ubuntu 10.04 dual-booted with Windows 7. How do I make Windows the default boot option? Which file do I edit?

---

### Post by zvacet on 2010-05-11
In synaptic install startup manager and with it make Windows default boot OS.

---

### Post by James78 on 2010-05-11
Open your text editor with root permissions, then edit GRUB_DEFAULT=0 in /etc/default/grub

If your first menu entry is Linux, and your 4th menu entry is Windows 7, then GRUB_DEFAULT=3. 0=1,1=2, etc.

---

### Post by auh2o on 2010-07-09
> **James78 said:**
> Open your text editor with root permissions, then edit GRUB_DEFAULT=0 in /etc/default/grub

If your first menu entry is Linux, and your 4th menu entry is Windows 7, then GRUB_DEFAULT=3. 0=1,1=2, etc.

That solution means that for every new kernel update or removal of old kernels, you'll have to edit /etc/default/grub, or the setting will be wrong.

Much better would be to set, as per GRUB help:

> GRUB_DEFAULT="xxxx" An exact menu entry, including the quotation symbols, may also be used. In this case, location in the menu will not matter. Example: GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"So what I want to know is exactly what to put in the quote to make Windows *always* start by default.

```
Found Windows 7 (loader) on /dev/sda1
```Is it "Windows", "Windows 7", "Windows 7 (loader)" or something else?

Edit: Well, it's not "Windows 7". What's Grub's internal name for the Windows image?

---

### Post by fidelfloris on 2010-07-09
Good evening,
 
I have a simular problem.
 
I also have Ubuntu and Windows 7 dualbooting.
 
But after installing Windows 7 I lost my grub menu with Ubuntu!
 
Can somebody explain me how to get it back?
 
I have Ubuntu on USB also.
(don't know if that can help?)
 
Greetings Fidel

---

### Post by auh2o on 2010-07-10
> **fidelfloris said:**
> I have a simular problem.

No, you don't. Your problem does not pertain to this thread. What you need to do is use the Live disc to reinstall Grub, and there are plenty of threads on that very subject here that will tell you how.

---

### Post by T34se on 2010-11-16
auh2o, I used: GRUB_DEFAULT="Windows 7 (loader) (on /dev/sda1)" and it works.

Yours will prob be the same but you can double check by checking the /boot/grub/grub.cfg file and looking for the Windows 7 entry, the entire name must be used between the quotes "Windows 7 (loader) (on /dev/sda1)"

---

