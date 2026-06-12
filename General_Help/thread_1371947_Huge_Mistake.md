---
title: "Huge Mistake"
date: 2010-01-04
forum: General Help
---

### Post by Final Version on 2010-01-04
I just downloaded Ubuntu 9.04 while using the 8.10 live cd. I was planning to burn it to a disc, but I forgot all about the live cd issue.

So is there anyway I can burn Ubuntu 9.04 without having to download it to a real os. Or can I make a bootable usb with the live cd of 8.10.

---

### Post by k64 on 2010-01-04
> **Final Version said:**
> I just downloaded Ubuntu 9.04 while using the 8.10 live cd. I was planning to burn it to a disc, but I forgot all about the live cd issue.

So is there anyway I can burn Ubuntu 9.04 without having to download it to a real os. Or can I make a bootable usb with the live cd of 8.10.

You can open a terminal on the Live CD and run "sudo update-manager -d" which will run a distribution upgrade on the CD itself. That way, you can update the CD. By the way, this will upgrade it to 9.10 "Karmic Koala", not 9.04.

---

### Post by Final Version on 2010-01-04
Thanks, but I just found System>Administration>Create A USB Startup Disc

Will I be able to install the os from this?

---

### Post by Final Version on 2010-01-04
I just tried the to Create a usb startup and the application just keeps crashing.

---

### Post by CharlesA on 2010-01-04
Do you have any other machines on the network? If you do, you can access them from the "network" under Places and copy the ISO to one of them temporarily.

---

### Post by Final Version on 2010-01-04
Nope, just my xbox 360. I have another machine hidden god knows where, with no os that I know of. And besides it doesn't have a cd burner.

---

### Post by Marrkk on 2010-01-04
a USB stick ?  a USB mobile phone with a memory card and
 room for a .iso on it ?

---

### Post by Final Version on 2010-01-04
No, a 1GB usb.

---

### Post by Marrkk on 2010-01-04
can you fit the .iso on the 1Gb stick ?
there is a way to install off of an a stick, but i'm not sure how.
i beleive grub2 will boot a .iso image.
not a lot of help i know :( , but u can at least save the iso and burn it to CD on another PC if you have access to one.

---

### Post by Final Version on 2010-01-04
This is my only PC with a burner.

---

### Post by Final Version on 2010-01-04
Oh yeah, when I hit create the program just crashes.

---

### Post by CharlesA on 2010-01-04
If there isn't any OS on the current machine, just install 8.10 and then burn the 9.04 iso.

---

### Post by Final Version on 2010-01-04
> **CharlesA said:**
> If there isn't any OS on the current machine, just install 8.10 and then burn the 9.04 iso.
I would, but to install or even use the cd live I need to use noapic, I do this with install, the from grub I select ubuntu and it asks me to enable noapic again, I have no idea how from grub.

**How do I enable noapic within grub.**

---

