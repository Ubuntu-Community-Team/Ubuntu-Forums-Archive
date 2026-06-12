---
title: "boot failure boots to dos"
date: 2009-11-16
forum: General Help
---

### Post by medic0079 on 2009-11-16
So have had a strange phenomenon start happening, I installed 9.10 using the upgrade. it worked fine for the first 2 weeks or so, but now when booting does not go to boot screen, it has the initial ubuntu logo, then goes to a dos looking sign in, when i sign in using name and password, it stays in dos, and does not continue to boot. any ideas?

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
That's not dos. It's bash. What happens if you type startx after you log in?

---

### Post by medic0079 on 2009-11-16
it then booted to my desktop, as normal, but asked for network password, once I entered my password it would not connect to the internet, after about 30 seconds the screen went black, then would do nothing, I rebooted again, and it booted normally. this is an intermittent problem.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Network password? Hmm... I have no idea why it would ask for a WPA password. I could see it asking for the root password which you set upon install. The fact that it drops to the shell intermittently would signify graphics card driver issues. Look around the forums for explanations of how to install and configure your graphics card. Also the same for the network access. Are you connecting via wired or wireless? A more detailed description of the system's hardware would help.

---

