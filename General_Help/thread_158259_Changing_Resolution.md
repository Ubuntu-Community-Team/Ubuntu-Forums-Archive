---
title: "Changing Resolution"
date: 2006-04-10
forum: General Help
---

### Post by danakatheone on 2006-04-10
OK, so I just installed Ubuntu, and I go into change the resolution. My monitor's native resolution is 1280x1024, but the highest resolution I'm allowed to set is 1024x768. Is there any way to force 1280x1024?

---

### Post by Bishop Hill on 2006-04-10
What graphics card do you use?

---

### Post by danakatheone on 2006-04-10
7800GTX, I just used the guide in here to install the newest Nvidia drivers.

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=danakatheone]7800GTX, I just used the guide in here to install the newest Nvidia drivers.[/QUOTE]
Use the following command:
> 
sudo dpkg-reconfigure xserver-xorg 

Try and fill in the answers the best that you can. When you get to the part that asks, "Select the resolutions that you would like to use." Uncheck ALL of them but the screen resolution that you want to use.

---

### Post by danakatheone on 2006-04-10
Thank you.

---

### Post by xXx 0wn3d xXx on 2006-04-10
[QUOTE=danakatheone]Thank you.[/QUOTE]
No problem, I'm here to help. :)

---

