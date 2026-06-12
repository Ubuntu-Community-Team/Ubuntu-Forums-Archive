---
title: "Natty Grub2 Problem"
date: 2011-09-08
forum: General Help
---

### Post by rolodoom on 2011-09-08
My current system is Ubuntu 11.04 64 bits.

I installed startupmanager to change the default OS to boot but is not working. Besides I just realized that the list that startupmanager shows me is not the same that grub shows me on boot.

I already tried to completely uninstall startupmanager.

¿Any idea how to fix it?
¿Maybe is better to go back to grub1?

---

### Post by Bodsda on 2011-09-08
> **rolodoom said:**
> My current system is Ubuntu 11.04 64 bits.
 
I installed startupmanager to change the default OS to boot but is not working. Besides I just realized that the list that startupmanager shows me is not the same that grub shows me on boot.
 
I already tried to completely uninstall startupmanager.
 
¿Any idea how to fix it?
¿Maybe is better to go back to grub1?
 
Just out of interest, does BootUpManager display the correct list?
I'm pretty sure ubuntu tweak can also provide this functionality.
 
Failing that, get down and dirty and edit the grub config file by hand.
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
 
Hope this helps,
Bodsda

---

### Post by rolodoom on 2011-09-08
¿¿¿why BootUpManager??? As far as I know the only things you see here are services.

Didn't find how on ubuntu tweak.

There are still kernels on grub menu that we're uninstall on the system!!!

---

### Post by Bodsda on 2011-09-08
> **rolodoom said:**
> ¿¿¿why BootUpManager??? As far as I know the only things you see here are services.
 
Didn't find how on ubuntu tweak.
 
There are still kernels on grub menu that we're uninstall on the system!!!
 
See if this makes more sense 
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
 
Kernels should be removed when you uninstall them... but as I said before, nothing is stopping you from removing them manually
 
Bodsda

---

### Post by rolodoom on 2011-11-19
The solution for me was to do it manually editing  the file:
```
sudo nano /etc/default/grub
```
Then modified the number for the Default boot. (4 for default win on dual boot)
```
GRUB_DEFAULT=4
```
and then update grub and reboot to test!
```
sudo update-grub
```

---

