---
title: "ntop hogging cpu after upgrade"
date: 2009-11-26
forum: General Help
---

### Post by fprintf on 2009-11-26
After my upgrade to Karmic Koala, my machine has been running really slowly. My conky script is showing ntop is constantly running and hogging up to 80%, but a minimum of 45% CPU. If I kill ntop it restarts on its own.

This is on a IBM T30 laptop with a PCMCIA wireless card. I am wondering if this is something to do with the wireless monitoring, but not sure. This is an upgraded system not a fresh install.

---

### Post by fprintf on 2009-11-27
So I narrowed it down to NTOP starting up whenever I resume from suspend. It definitely takes the balance of the available CPU, so pegs the CPU at 100% for as long as I keep it running. The only way to get rid of it is to kill the pid via jobs.

For now I have removed the package. This doesn't feel like the right thing to do, but it works. I am assuming ntop is part of the default install and not something I put on the system or inherited from the prior install.

---

### Post by SecretCode on 2009-12-31
Just for the record, I'm affected by this too. And [Bug #461141 in ntop (Ubuntu): &#8220;ntop produces 100% CPU load after suspend&#8221;](https://bugs.launchpad.net/ubuntu/+source/ntop/+bug/461141) documents it as an issue.

---

### Post by asenzz on 2010-08-16
I'm having this same problem. I need to do a /etc/init.d/ntop restart after hibernation to get back to normal CPU usage.

---

### Post by asenzz on 2010-08-16
I'm having this same problem. I need to do a /etc/init.d/ntop restart after hibernation to get back to normal CPU usage.

---

### Post by asenzz on 2010-08-16
I'm having this same problem. I need to do a /etc/init.d/ntop restart after hibernation to get back to normal CPU usage.

---

### Post by asenzz on 2010-08-16
I'm having this same problem. I need to do a /etc/init.d/ntop restart after hibernation to get back to normal CPU usage.

---

### Post by fprintf on 2010-08-16
I simply removed NTOP from my installation.

---

