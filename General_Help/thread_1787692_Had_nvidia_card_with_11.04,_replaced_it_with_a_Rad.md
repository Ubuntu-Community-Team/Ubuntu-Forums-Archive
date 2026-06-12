---
title: "Had nvidia card with 11.04, replaced it with a Radeon without removing nvidia drivers"
date: 2011-06-21
forum: General Help
---

### Post by garyiskidding on 2011-06-21
Hi,

I'm still new to unix and ubuntu.

I had an nvidia card installed on my ubuntu-windows dual boot system, and with that, i had enabled the nvidia drivers.

I then installed an AMD radeon card, without removing the nvidia drivers. Now, when i start ubuntu, i just do not get a graphical user interface, but get the shell/text based interface. 

I am guessing that it is because the installed nvidia drivers causing problems with a radeon card. How do i un-install them and get the user-interface back? Is there a way to run it without using the nvidia drivers?

Thanks
Gary

---

### Post by pqwoerituytrueiwoq on 2011-06-21
if you installed the driver via the gui
sudo apt-get remove nvidia-current nvidia-settings
if you instlalled via nvidia's run file
sudo nvidia-installer --uninstall

---

