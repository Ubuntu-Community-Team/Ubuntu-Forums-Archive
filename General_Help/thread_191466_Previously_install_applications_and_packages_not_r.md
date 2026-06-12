---
title: "Previously install applications and packages not recognized"
date: 2006-06-07
forum: General Help
---

### Post by tehquickness on 2006-06-07
I had to reinstall windows on my windows partition and it obviously changed the mbr. So to correct this I used the bootable to cd to reinstall grub. This worked, however for some reason the synaptic package manager and the add/remove application menu dont recognize the applications and packages that I had previously installed. What did I do wrong and how can I fix this?

---

### Post by givré on 2006-06-07
What is the error you have with apt-get?

---

### Post by tehquickness on 2006-06-07
I am afraid I am not sure what you mean. What command would I be doing with apt-get?
I think that I when I reinstalled the boot, it might have reinstalled a new kernel or something. would that make this happen?

---

### Post by givré on 2006-06-07
Synaptic use apt-get, so if you do someting like
```
sudo apt-get remove one_of_a_package_you_want_to_uninstall
```
in a terminal, You will know why it doesn't work.

In linux, when an application doesn't work or freeze, try to run it via a terminal, you will have the error in output, it's really usefull

---

### Post by givré on 2006-06-07
[QUOTE=tehquickness]
I think that I when I reinstalled the boot, it might have reinstalled a new kernel or something. would that make this happen?[/QUOTE]
It depends of the thing you did to reinstall the boot, but if you simply reinstall grub, definitly not. Say here what you did. (and in any way, you can install every kernel you want, it will not affect your package manager

---

### Post by tehquickness on 2006-06-07
This is what it says. I know I have neutrino install bc I can use it.

Package neutrino is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

That is what it says. I didnt have a live cd on hand so i saw that you could just use the install cd, mount the partitions but not format them, and then have it install grub. However I think it reinstalled more than grub. Maybe it reinstalled some Ubuntu stuff as well, like the apt-get files.

---

### Post by givré on 2006-06-07
[QUOTE=tehquickness] However I think it reinstalled more than grub. Maybe it reinstalled some Ubuntu stuff as well, like the apt-get files.[/QUOTE]
If you just did grub-install, i don't that i do more.
I suggere you to reboot, if its not already done

---

