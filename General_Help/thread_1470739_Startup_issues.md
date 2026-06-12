---
title: "Startup issues"
date: 2010-05-03
forum: General Help
---

### Post by cloudslayer on 2010-05-03
Hi,

I've recently installed the new Kubuntu 10.04 and I'm quite impressed with it. It finally solved my networking problems and ATI effects problems. Sadly, as ever with Linux it seems to be two steps forward and one back. In this case it's some major boot problems I'm having.

The first boot: After grub I suddenly get a black screen and I'm unable to do anything.

The second boot: The normal splash screen appears and KDE starts to boot. This however starts to hang due to a problem with .ICEAuthority, which apparently became root property so deleting it solved that problem.

Third boot: Everything works like it should and I'm having the best Linux experience ever...

This this entire cycle doesn't happen every time, and sometimes it just works like it should, but it did at least happen twice in the last two days...

Does anyone know where this problem could be coming from and how I can figure out what's going on when the screen gets blank?

---

### Post by dino99 on 2010-05-03
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

### Post by cloudslayer on 2010-05-03
> **dino99 said:**
> sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

What exactly is that supposed to do? Nothing happened (the first command didn't have any output, the last had output "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.")

---

