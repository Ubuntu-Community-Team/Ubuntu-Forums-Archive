---
title: "touchpad driver gone. How do I get it back."
date: 2011-06-17
forum: General Help
---

### Post by baillou2 on 2011-06-17
I was having touchpad issues out of the blue so I tried a fix where I do this:  sudo sh -c "echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe" 

Unfortunately I only found out afterward that this replaced my touchpad driver with the mouse one, and as a result I don't even have the tab menu that is normally under the "mouse settings". 

How do I undo this?? Please help!

---

### Post by tredegar on 2011-06-17
You could try
```
sudo mv /etc/modprobe.d/psmouse.modprobe   /home/baillou
```
and then reboot.

---

### Post by baillou2 on 2011-06-18
That solution didn't work at all. I wish I knew what I did in the first place. What I need to do is reinstall the module for the touchpad. How do I do this??

---

