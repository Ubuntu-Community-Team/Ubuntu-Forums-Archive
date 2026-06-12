---
title: "Booting problems"
date: 2011-08-23
forum: General Help
---

### Post by apacketofsweets on 2011-08-23
Ubuntu no longer boots up on my Archos 10 netbook, it's been working fine for the whole month I've had it but now it simply sticks to the Ubuntu loading screen and doesn't progress further.

Windows still boots fine so my guess is it's not a hard drive failure that's causing it. Any ideas?

---

### Post by Basher101 on 2011-08-23
Did you make any update or anything of that sort? like installing a driver?
Do you receive any error message or does it simply get stuck on the plymouth?

---

### Post by apacketofsweets on 2011-08-23
I've done no updating or anything out of the ordinary, it simply gets stuck on the plymouth.

---

### Post by Basher101 on 2011-08-23
try booting into recovery and then start your session

---

### Post by apacketofsweets on 2011-08-23
Booting into recovery results in the machine shutting down immediately, perhaps a re-install is in order?

---

### Post by sikander3786 on 2011-08-23
> **apacketofsweets said:**
> Booting into recovery results in the machine shutting down immediately, perhaps a re-install is in order?
Almost all the time, one can repair a Linux install without needing to re-install it but that is your own preference of course. Trying to repair a broken PC needs some work and obviously, time also. Whereas re-install is easier and less time consuming. If there weren't a lot of configuration/customization involved, re-install would be an easier option.

If you want to repair it:

How many Kernels are there in the Grub menu? If more than one, did you try booting an older one?

If that doesn't help, highlighting the Ubuntu entry in Grub, press 'e' to edit it. Remove the words 'quiet splash' and type 'nomodeset' in their place. Press Ctrl + X to continue boot. How far does it get? Can you see some errors on the screen?

The changes you make to your Grub entry are just temporary. They would revert to the original entry once your reboot your PC so you don't need to fear about messing it further.

---

