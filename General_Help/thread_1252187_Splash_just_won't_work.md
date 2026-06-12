---
title: "Splash just won't work"
date: 2009-08-28
forum: General Help
---

### Post by Lockheed on 2009-08-28
I tried many methods I could find on these forums but I still cannot get splashscreen during bootup.
I installed usplash and startupmanager. 
I properly installed new splash screens and... nothing.
I played around with dpkg-reconfigure linux-image-2.6.30.1
I edited /etc/initramfs-tools/modules

And nothing. What else can I try?

---

### Post by gastly on 2009-08-28
Have you tried checking if there's a **nosplash** option in the kernel options in your /boot/grub/menu.lst. If it's there then just remove it and the splash will work :)

---

### Post by Lockheed on 2009-08-28
> **gastly said:**
> Have you tried checking if there's a **nosplash** option in the kernel options in your /boot/grub/menu.lst. If it's there then just remove it and the splash will work :)
Sure. I don't have that option.
```
kernel		/boot/vmlinuz-2.6.30.1-azure root=UUID=087b9e3b-a65c-4890-9b0e-de019b0fff18 ro quiet splash

```
Is "quite splash" ok?

---

### Post by rbc on 2009-08-28
Yes. quiet splash is what is should be. This may be a long shot, and my aging brain may be remembering something that didn't actually happen, but I seem to recall reading somewhere that if swap's UUID doesn't match its UUID in menu.lst, then that would cause such a situation. Any smarter folks out there want to confirm that, even if it is not Lockheed's issue?

---

### Post by Lockheed on 2009-08-29
> **rbc said:**
> Yes. quiet splash is what is should be. This may be a long shot, and my aging brain may be remembering something that didn't actually happen, but I seem to recall reading somewhere that if swap's UUID doesn't match its UUID in menu.lst, then that would cause such a situation. Any smarter folks out there want to confirm that, even if it is not Lockheed's issue?
Why would there be swap in menu.lst? Isn't it just for bootable partitions?

---

### Post by Lockheed on 2009-08-30
I have added "resume=" with proper partition UUID to the kernel line in menu.lst, but I still cannot see any splash image.

---

