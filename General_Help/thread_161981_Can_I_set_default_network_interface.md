---
title: "Can I set default network interface?"
date: 2006-04-18
forum: General Help
---

### Post by mark_g on 2006-04-18
I have a wired network card (eth0) and a wireless (eth1). I only use the wireless one, so a lot of programs I use demand I specify that I want to use the eth1 or else it'll just use eth0, which does nothing of course.
Can I set eth1 to be the default network interface?

---

### Post by pitkali on 2006-04-18
Try System > Administration > Networking, and just deactivate eth0. Won't that help? You could also edit /etc/iftab and switch interface names found there, so that eth0 would be your wireless interface.

---

### Post by mozetti on 2006-04-18
Isn't there in option in the Sys->Admin->Networking, at the bottom, to specify a default?

---

### Post by pitkali on 2006-04-18
Default **gateway device**, yes. Though the original question doesn't seem to concern this...

---

### Post by echo $USER on 2006-04-18
You can edit /etc/network/interfaces and just comment out the devices you don't want to be default.  That's how I got my wireless ath0 to be the default by commenting out eth0.

---

### Post by mark_g on 2006-04-18
Thank you for your help, editing the iftab file was the solution I was searching for.

---

