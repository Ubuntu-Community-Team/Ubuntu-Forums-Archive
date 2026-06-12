---
title: "command 'switch' doesn't run gtk-theme-switch"
date: 2010-03-07
forum: General Help
---

### Post by PhoHammer on 2010-03-07
So I want to use gtk-theme-switch to change my theme in openbox
 (would rather not use any gnome/kde/etc.. tools for this), but 
after installing it I cannot get it to run:


> tr@linux:~$ sudo apt-get install gtk-theme-switch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk-theme-switch is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But when I try to run it, I get:
> 
tr@linux:~$ switch
No command 'switch' found, did you mean:
 Command 'swatch' from package 'swatch' (universe)
switch: command not found
tr@linux:~$ switch2
switch2: command not found
tr@linux:~$ 


Any ideas?

---

### Post by robertwall on 2010-03-08
The program name you're looking for is ```
gtk-theme-switch2
```, according to the list of files in the package. You can find that list with ```
dpkg -S gtk-theme-switch
``` on the command line, or the "Installed Files" tab of the "Properties" window in Synaptic.

---

### Post by PhoHammer on 2010-03-08
I tried to use gtk-theme-switch2, but it wouldn't work for me. Anyways, I decided to go with lxappearance. It fits the bill.

Thanks, though!!

---

