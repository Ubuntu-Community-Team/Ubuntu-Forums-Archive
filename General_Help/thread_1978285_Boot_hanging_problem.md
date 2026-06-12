---
title: "Boot hanging problem"
date: 2012-05-11
forum: General Help
---

### Post by Intoxication on 2012-05-11
I installed some updates last night. The only thing I'm able to remember was one of them said linux headers. Now it hangs everytime at boot. I can't even get into the terminal after it hangs.
 
here's what I'm able to see:
 
*Setting sensors limits [OK]
*Stopping load modules from /etc/modules [OK]
[15.601119] SP5100 TCO timer: MMIO adress 0xb8fe00 already in use
*Starting System V runlevel compatibility [OK]
*Stopping automatic crash report generation [FAIL]
*Starting eCryptfs [OK]
*Starting ACPI daemon [OK]
*Starting save kernal messages [OK]
*Stopping CPU interrupts ballancing daemon [OK]
Mountfall: Disconnected from plymouth
 
That's everything it'll do. After that, I can't do anything.
 
Ubuntu 11.04
 
I would appreciate it if someone could help me with this. Thank you.

---

### Post by cmont899 on 2012-05-11
The forst thing that should appear when the OS starts to boot is a grub splash where you can select the kernel you boot with. Try selecting the previous kernel version and see if the error persists.

Chris

---

### Post by Intoxication on 2012-05-11
Chris,
 
That screen never shows itself anymore. It goes straight to the Unbuntu loading screen right before the login screen (with the dots under the words Ubuntu indicating that it's loading). That's where it stops. 
Is there another way I can get to the grub spash? Maybe a hotkey or something?
 
 
Edit:
 
Ok I searched google and it said to hold down the Shift key. I did that and sure enough it worked, I'm able to boot now. I appreciate your help Chris, thank you!

---

