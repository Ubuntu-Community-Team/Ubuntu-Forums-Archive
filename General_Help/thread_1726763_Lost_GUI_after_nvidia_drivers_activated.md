---
title: "Lost GUI after nvidia drivers activated"
date: 2011-04-11
forum: General Help
---

### Post by Elitenoname on 2011-04-11
So i installed Ubuntu 10.10 did updates all was fine. when i went to activate the nvidia driver it install but upon restart i lost my GUI. I have a nvidia ion next gen graphics card. Running desktop 10.10 with intel atom dual core and 2gb of ram

NOTES: 
1.) sudo service gdm start states that the gdm service is already running

2.) ctr + alt + f7 does nothing and along with that all the other alt + f keys do not have a GUI

3.) i can log in and use the OS via command line 

4.) other things i have tried is the sudo apt-get install nvidia-current just led to the same results

open to suggestions

---

### Post by TeoBigusGeekus on 2011-04-11
```
sudo rm /etc/X11/xorg.conf
sudo reboot
```
Upon reaching your desktop
```
gksu nvidia-settings
```
Try to configure your display from there. Once done, click "Save to X configuration file". Reboot. Post back.

---

### Post by Elitenoname on 2011-04-11
```
sudo rm /etc/X11/xorg.conf
```
that did not work got a message stating that the directory could not be located

and then the ```
gksu nvidia-settings
``` also came back with an error and i am pretty sure that has to do with the first line having and error

NOTE: don't know if this make a difference but i install ubuntu within windows.

---

### Post by TeoBigusGeekus on 2011-04-11
Oops... a wubi installation eh?
Sorry, mate, I haven't got a clue... 
Anyone else?

---

### Post by Elitenoname on 2011-04-11
its ok i had it working as a full ubuntu on my laptop but i needed windows so i figured why not try this and well, not working out too good there a better way to dual boot this? not a big fan of using virtual box or any virtual machine.

---

### Post by TeoBigusGeekus on 2011-04-11
Just dual boot. Install windows first (apparently you have) and then install ubuntu side by side.
[Here's]("https://help.ubuntu.com/community/WindowsDualBoot") a guide on how to do it.

---

### Post by MrRichard on 2011-04-11
I agree, wubi caused too many problems with me. Slowness was one of my big issues.
If you decide you want to go back to an all-Windows computer, there's always tutorials to help you out, or you can come back here and ask us :popcorn:

---

