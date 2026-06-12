---
title: "Update Manager + Firefox = slow"
date: 2009-10-27
forum: General Help
---

### Post by Anonymousable on 2009-10-27
If I install updates using synaptic or the update manager (yes, it's practically synaptic too) while browsing the web, firefox starts to run really slowly. The strange thing is, this *doesn't* happen if I install the updates using apt-get dist-upgrade.

Can anyone explain this?
Thanks in advance.

---

### Post by Anonymousable on 2009-10-27
bump, can anyone explain this behavior?

---

### Post by philinux on 2009-10-27
> **Anonymousable said:**
> If I install updates using synaptic or the update manager (yes, it's practically synaptic too) while browsing the web, firefox starts to run really slowly. The strange thing is, this *doesn't* happen if I install the updates using apt-get dist-upgrade.

Can anyone explain this?
Thanks in advance.

Would help to see your pc specs.

---

### Post by Anonymousable on 2009-10-28
My CPU is an Intel Core 2 Quad CPU Q8200, 2.33GHz, I have 4GB of RAM, and my graphics card is an nVidia GeForce 7300 GS. 
Any more details needed?

I'm using the beta of ubuntu 9.10, and this didn't happen in 9.04.

---

### Post by philinux on 2009-10-28
Check System>admin>hardware drivers and make sure you got an active graphics driver.

If all ok then see below.

Reboot to get a clean startup. Run the command ```
top
```
in a terminal. Try to recreate the problem and watch the terminal to see whats eating resources.

---

### Post by Anonymousable on 2009-10-28
Well, I'm pretty sure it's the synaptic frontend to apt/dpkg.

I have the proprietary graphics drivers installed for my card (using jockey-gtk), and it's used by all those different programs that use 3D hardware acceleration, so yes.

I need to wait for some more updates to come out (not long until a bunch come out), I'll post with more info soon (and use htop, it's easier :P )

---

### Post by Anonymousable on 2009-10-30
OK, I've tested it... And for some reason the X server starts using insane amounts of CPU power when synaptic is working.

Any ideas?

---

