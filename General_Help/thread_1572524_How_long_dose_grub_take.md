---
title: "How long dose grub take"
date: 2010-09-11
forum: General Help
---

### Post by Bananasdoom on 2010-09-11
I have just installed windows 7 witch of coarse in great windows style killed my fun (metaphorically i was planing on playing games on it) so I have had to burn a Linux disk to run a fix for my grub. Now i have started the fix i get this ```
Probing devices to guess BIOS drives. This may take a long time.
``` I have been waiting for 4 hours now i restarted the first one because i thought it was hung ( the cursor was flashing so i am not sure why i did it). So how long is ```
"a long time"
``` ?? Coz i have work to do

---

### Post by coffeecat on 2010-09-11
Do you mean that you had a working Ubuntu system and that you then installed Windows, and it overwrote grub in the MBR? And what are you doing to "fix" grub? I've never seen that 'Probing devices...' message before.

If you are simply trying to reinstall grub after Windows overwrote the MBR, have a look here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

This is for Grub2. If your Lucid Lynx was a fresh install, that would be correct, but if you started with Jaunty Jackalope (or earlier) and upgraded through Karmic, then you need instructions for legacy grub.

---

### Post by ajgreeny on 2010-09-11
The message you get seems to indicate more than just a grub problem, and I would suggest you restart the machine and go into the BIOS and search around for the disk detection part.  Try a few different settings there, but remember what it was set to so you can get back to the current situation if you need to do so.

---

### Post by Bananasdoom on 2010-09-11
> **coffeecat said:**
> Do you mean that you had a working Ubuntu system and that you then installed Windows, and it overwrote grub in the MBR? And what are you doing to "fix" grub? I've never seen that 'Probing devices...' message before.

If you are simply trying to reinstall grub after Windows overwrote the MBR, have a look here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

This is for Grub2. If your Lucid Lynx was a fresh install, that would be correct, but if you started with Jaunty Jackalope (or earlier) and upgraded through Karmic, then you need instructions for legacy grub.

Thanks heaps for the link i was installing GRUB legacy now lets see if grub 2 works

---

