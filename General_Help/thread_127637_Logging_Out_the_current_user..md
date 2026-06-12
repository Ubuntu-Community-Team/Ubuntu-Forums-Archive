---
title: "Logging Out the current user."
date: 2006-02-09
forum: General Help
---

### Post by Theely on 2006-02-09
I seem to have to messed something up and I'm not exaclt sure how. :p 

Whenever I go to log out a user the login manager never appears anymore. It brings me straight to the command prompt instead. The odd thing is that if I reboot my system the login manager does appear. But thats the only time.

Any ideas on how to bring the manager back up? I know this a pretty lame post since I'm not sure what caused it to go away in the first place. :(

---

### Post by Derek Djons on 2006-02-09
I've experienced the same problem again restarting the X-Server using CTRL+ALT+DEL.

In my case it was linked to resolution(management) problems. Can you post the following specs. If there are similarities in hardware between us then we're one step further.

- Videocard
- Drivers using / installed
- Motherboard chipset

---

### Post by Theely on 2006-02-09
Mine happened to fixed itself for logging out from the System menu, haven't tried cntl+alt+backspace yet though.

Video Card = nvidia geforce4 mx 440
driver = which ever one you can download from Synaptic atm.
Mobo = GigaByte K8 Triton GA-K8U-939 w/ ULi M1689 chipset

---

### Post by Derek Djons on 2006-02-09
Totally none similarities. I'm having:

Video Card: ATi Radeon 9700 Pro.
Driver: Synaptic drivers.
Motherboard: MSI K8N Series with a VIA Chipset.

Hoped it would bring something up, but unfortunatelly it's probably a much deeper problem.

---

### Post by Theely on 2006-02-09
As for me saying that it fixed itself on my system, I think its only because I rebooted. After the reboot I could use the Log Out from the System menu and it would bring me to the login screen. I then tried Ctrl+Alt+Backspace and it did again bring me to the prompt login. I would login then "startx" and be back in Gnome. If I tried to log out via the System after all of that, its broken and sends me to the command line login instead of the graphical login.

So yeah, its not fixed like I thought it was. :(

---

