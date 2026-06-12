---
title: "Font garbled beyond readability"
date: 2012-09-15
forum: General Help
---

### Post by Delocaz on 2012-09-15
I have this old Compaq (Yes, before it was HP) just lying around and i decided to turn it unti a server. I downloaded the mini/netinstall iso (cd-drive is broken, can't boot from usb) and loaded that into RAM with UNetbootin. I installed it fine. Then after i rebooted into the installed system, everything was garbled. The computer has a Pentium III, 1.0GHz, graphics card unknown. As for the age? Think "Came with Windowd 2000".

The bootup sequence itself (GRUB) is fine, the garble occurs just after GRUB.
If you wait a few minutes, suddently the screen will turn all write with black vertical stripes.

I was going to SSH into it (don't have a GUI, just command line), but withuot ipconfig i can't get the IP.
Don't bother asking me to edit a file because i can't without being able to see what i'm typing.

I attached some screenshots (literally taken by my phone) below.

EDIT: I fixed it. I went into the recovery console, it worked, i installed ssh and used ifconfig. I then SShed into it from mo other computer, restarted the server and voila. Somehow, it now works perfectly fine, even without recovery mode.

---

