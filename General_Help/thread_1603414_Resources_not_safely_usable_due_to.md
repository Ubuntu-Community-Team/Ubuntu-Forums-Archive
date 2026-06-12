---
title: "Resources not safely usable due to"
date: 2010-10-22
forum: General Help
---

### Post by sk8erbender on 2010-10-22
Hey,everyone! I've got Ubuntu 10.10 , when loading I see the following message:
"atk: Resources not safely usable due to acpi_enforce_resources kernel parameter"
What does it mean and do I need to fix it?
Sorry , I didnt find anything about it in search.

---

### Post by jerrrys on 2010-10-23
if your computer is working ok then it sounds like a glitch acpi

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=acpi+enforce+resources+kernel+parameter&as_qdr=all&sa=Google+Search&lang=en#1383](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=acpi+enforce+resources+kernel+parameter&as_qdr=all&sa=Google+Search&lang=en#1383)

---

### Post by sk8erbender on 2010-10-23
Tyvm! Sloved this nut msg by doin the following:

- sudo gedit /etc/default/grub
- change GRUB_CMDLINE_ LINUX="acpi_enforce_resources=lax" to GRUB_CMDLINE_ LINUX="acpi_enforce_resources=STRICT"
- save and close
- run sudo update-grub
- reboot

doin acpi_enforce_resources=no or =lax ;it didnt work for me untill I put STRICT in it.

---

### Post by jerrrys on 2010-10-23
nice job...please to remember to mark your thread as solved

---

