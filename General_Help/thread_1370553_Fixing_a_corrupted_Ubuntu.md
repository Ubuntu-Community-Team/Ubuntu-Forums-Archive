---
title: "Fixing a corrupted Ubuntu?"
date: 2010-01-02
forum: General Help
---

### Post by jimford on 2010-01-02
Ubuntu 9.10 was working fine on a laptop until recently when it wouldn't complete booting - ending up with a blank screen. I think there's a problem with the Xserver and need to get into a console to fix it.

I've tried using recovery mode from Grub, but get a box stating:

"Ubuntu is running in Low-graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You need to configure these yourself"

The box is a clear hi-res graphic one and the touch pad and keyboard work OK, in spite of the above warning!

On selecting the 'OK' box, it proceeds to another:

"What would you like to do?
* Run Ubuntu in Low-graphics mode for just one session.
* Reconfigure graphics.
* Troubleshoot the error.
* Exit to console."

Whatever I do, I end up with a blank, inert screen.

The boot process seems to be largely completed, as the network is up and I can ping it. I've tried to ssh into the machine, but was unable to do so.

I can run DSL and mount the hard drive. I then need to fix the boot process, so it ends up with a console to enable me to re-install the Xserver. I've googled for booting into a console and tried most if not all solutions offered, without success!

Has anyone any ideas that are guaranteed to Ubuntu 9.10 to boot into a console, please?

Jim

---

### Post by koma77 on 2010-01-02
I'd use a live CD to boot the machine and then delete the xorg.conf file...

If that doesn't work, maybe a live CD and a changeroot can be used to reinstall packages etc?

---

### Post by celticbhoy on 2010-02-12
I have a similar problem, but I can get to the console via recovery --> drop to network root. How do I re-install the xserver?

---

