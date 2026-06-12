---
title: "Ubuntu 12.04 [Kernel 3.4] hangs at boot."
date: 2012-07-22
forum: General Help
---

### Post by Superpelican12 on 2012-07-22
My Ubuntu/Win7 dualboot Asus laptop(K53SJ-SX216V) won't boot Ubuntu (kernel 3.4 from official Ubuntu kernel ppa) anymore. It all started when I suspended my laptop for lunch. And when I came back and started the computer again "networking was disabled" and Ubuntu 1204 refused to connect to my home WiFi network in Unity. So I logged out and tried XFCE: exactly the same.
I had already re-enabled networking. But I still wouldn't connect. So I decided to reboot the computer. But the "log out"-button in XFCE didn't do anything. So I decided to reboot with "sudo reboot".

But the "Ubuntu logo and "moving white and purple spots"" kept showing. So I held the power button to force shutdown the laptop. After that I turned on the laptop again but doesn't come further than a black screen with white letters. After I a little while I the white mouse cursor appears and I hear the sound that you normally hear at the login screen. But the black screen is still there...

I have booted several times.

---

### Post by GreatDanton on 2012-07-22
During the boot hold shift and you will enter into Grub menu. After that select kernel 3.2 which is the official for Ubuntu 12.04. This is not a solution but only a workaround.

---

### Post by Superpelican12 on 2012-07-22
It works indeed with kernel 3.2, but I've been using kernel 3.4 for months. How can it suddenly stop working?

Thanks anyway. Now I can at least enjoy Ubuntu again. I don't really need kernel 3.4, but I read in the release notes that it featured a lot of enhancements (especially in terms of power effiency).

Hopefully they at least fix Linux 3.4 for Ubuntu 12.10...

---

