---
title: "Rescuing Files"
date: 2009-12-06
forum: General Help
---

### Post by WriYeDannii on 2009-12-06
Don't know if this is the right forum...
 
With today's update I've managed to lose access to ubuntu but I need to retrieve the files stored on the ubuntu side, any ideas how I do this?
 
I've tried booting from a live CD but it tells me I need to unistall the copy already on the computer. Also tried installing some programs but no of them have worked yet.
 
Any help appreciated. Thanks

---

### Post by mr clark25 on 2009-12-06
you should be able to view your HDD under "places" when you boot from the live cd. click "home" and then your user name and all of your files should be right there for you to copy.

---

### Post by WriYeDannii on 2009-12-06
It won't let me boot from the Live CD unless I unistall the current version on my computer... which I assume means I'll lose all my work anyway.

---

### Post by audiomick on 2009-12-06
Are you trying to boot into "Try Ubuntu without changing the computer", or what ever similar name to that it has? This option starts from the cd, and definitely does not want to install or uninstall anything.
This is what was meant.

---

### Post by lisati on 2009-12-06
Are you running the CD within Windows???????? Did you install Ubuntu "within" Windows using Wubi?

---

### Post by WriYeDannii on 2009-12-06
Yes i was using the 'try ubuntu' option on the disk. it is still telling me that i need to unistal the current version
 
Yes Ubuntu is installed using Wubi installer. It's worked fine until the update today.
 
Yes i am running the Cd in windows as it doesn't load up onto the boot menu... all i get is vista or ubuntu - which is corrupted at the moment

---

### Post by audiomick on 2009-12-06
OK. You need to go into the BIOS and change the boot order so that the computer will start from the CD before the boot loader starts. This loads an Ubuntu into the RAM, and it runs from there. This _does nothing_ to change the current installation on the computer.

From here, you can copy out the files from your Wubi installtion, if I have understood the previous posts correctly.

---

