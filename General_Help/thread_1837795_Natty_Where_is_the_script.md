---
title: "Natty: Where is the script"
date: 2011-09-02
forum: General Help
---

### Post by tweakmy on 2011-09-02
Where is the location of script where it writes the entry into the /etc/mtab and creation of the /media/<uuid>???

I know there is another way to edit the /etc/fstab to fix the mounting folder. But it would like to use still the traditional way of ubuntu but I would like to tweak so that any usb drive that is automounted is not readonly.

I am doing for my's pc. She is not very much into so much of command and typing. She is just normal user. So, I would like to automate for her.

---

### Post by dcstar on 2011-09-03
> **tweakmy said:**
> Where is the location of script where it writes the entry into the /etc/mtab and creation of the /media/<uuid>???

I know there is another way to edit the /etc/fstab to fix the mounting folder. But it would like to use still the traditional way of ubuntu but I would like to tweak so that any usb drive that is automounted is not readonly.


If USB drives are mounted "readonly" then it is most likely that is because the filesystems are corrupt - probably because they were previously removed incorrectly.

You do **not** stuff around with perfectly good system functions to get around the symptoms of another problem.

---

### Post by coffeecat on 2011-09-03
> **dcstar said:**
> 
You do **not** stuff around with perfectly good system functions to get around the symptoms of another problem.

+101!

@tweakmy, have you by chance installed the application usbmount? If you have, then uninstall it.

---

