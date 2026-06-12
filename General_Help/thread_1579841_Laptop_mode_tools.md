---
title: "Laptop mode tools"
date: 2010-09-22
forum: General Help
---

### Post by thefallofroy on 2010-09-22
I downloaded this in hopes that it would help and make a difference in my battery life. I installed the debian package like it said from the website by manually typing in what it said in a terminal. After this, it seemed to have installed properly however it does not seem like it is working. And now when i try to have linux do it (by double clicking on the package) I get an error that says "**Error: Breaks existing package 'pm-utils-powersave-policy' conflict: laptop-mode-tools ()**"

So does this mean laptop mode tools was indeed installed correctly? And if so how do I know if it's actually working? 'Cause like I said it doesn't seem like its making much of a difference in saving my battery life...

Thanks in advance

---

### Post by thefallofroy on 2010-09-22
Bump

---

### Post by mikewhatever on 2010-09-23
> **thefallofroy said:**
> I downloaded this in hopes that it would help and make a difference in my battery life. I installed the debian package like it said from the website by manually typing in what it said in a terminal. After this, it seemed to have installed properly however it does not seem like it is working. And now when i try to have linux do it (by double clicking on the package) I get an error that says "**Error: Breaks existing package 'pm-utils-powersave-policy' conflict: laptop-mode-tools ()**"

So does this mean laptop mode tools was indeed installed correctly? And if so how do I know if it's actually working? 'Cause like I said it doesn't seem like its making much of a difference in saving my battery life...

Thanks in advance

What web site and what did it say?
While Ubuntu is Debian based, installing Debian packages in Ubuntu is not recommended, especially since laptop-mode-tools for Ubuntu is in the repositories.

---

### Post by thefallofroy on 2010-09-23
Says right here they recommend using the debian packages, so I just did what it recommended... and plus I tried doing what it says first (to edit the acpi-support file) but it wouldnt let me edit it, and I couldnt figure out how to so i just said screw it and did it the debian way.

[http://samwel.tk/laptop_mode/packages/ubuntu](http://samwel.tk/laptop_mode/packages/ubuntu)

---

### Post by mikewhatever on 2010-09-23
I've just noticed that the thread's tag says 'wubi'. If you think you have excessive disk usage, your wubi installation might be responsible for that. Higher disk usage is mentioned in wubi's FAQ.

The laptop-mode-tools package in Ubuntu is the latest version, and, apparently, is installed by default in Karmic, but not engaged. You didn't need to install the Debian package, just needed to turn the laptop mode on. Once turned on, look through the config file - /etc/laptop-mode/laptop-mode.conf for desired option.

In order to edit system files in Ubuntu, escalation of privileges is required, in other words, 
**gksudo gedit /etc/default/acpi-support**  .

---

### Post by thefallofroy on 2010-09-23
Ok, so I edited the acpi-support file, but how do I enable laptop mode?

Also I dont have a laptop-mode directory in the etc folder

---

### Post by thefallofroy on 2010-09-27
Scratch my last post about the acpi-support file. I installed laptop mode tools through synaptic and I now have the laptop-mode file you were talking about. I looked through it and found the "enable_laptop_mode" option and the value is equal to one. This means it is enabled, correct?

---

### Post by thefallofroy on 2010-10-01
Bump

---

