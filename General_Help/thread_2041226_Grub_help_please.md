---
title: "Grub help please"
date: 2012-08-12
forum: General Help
---

### Post by cowboy7305 on 2012-08-12
Edit the file /etc/default/grub with "gksudo gedit /etc/default/grub"
    Find the line that starts with "GRUB_TIMEOUT"
    Change the valule from 10 to -1 (that's minus one not minus L)
    Run the command "sudo update-grub" in a terminal.

gksudo gedit /etc/default/grub

trying to use the above line to do the value change 
using LUBUNTU 12.04 on a Dell 530
i put the command in to the terminal and my password but it does not come up with any thing 
any help thanks

sudo gedit /etc/default/grub
tried this and still nothing get this 
sudo: gedit: command not found

---

### Post by claracc on 2012-08-12
To edit grub in /etc/default/, lubuntu 12.04, you will have to use the file editor leafpad (it is the default one).

If you want to use gedit you will have to install it, in a xterm you run:

sudo apt-get install gedit

---

### Post by cowboy7305 on 2012-10-08
many thanks

---

