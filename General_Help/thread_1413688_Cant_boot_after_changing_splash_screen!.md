---
title: "Cant boot after changing splash screen!"
date: 2010-02-22
forum: General Help
---

### Post by robembra on 2010-02-22
Hi,
 
My friend was showing me how to change the splash screen and used a app called start up manager (SUM).
 
He changed the resolutions for GRUB and something else. The GRUB screen resolutions has changed fine but after that I get a line of text which I cant read as its too quick.
 
Please help as my friend has decided not to anymore.... :( :( :(
 
 
Thanks

---

### Post by Muscovy on 2010-02-22
It sounds like it could be the resolution. I don't know where you can find the file to change that. If you can't boot, you'll have to go in and fix it with a LiveCD.

---

### Post by robembra on 2010-02-22
On boot it says:
 
**vga=795 is deprecated. Use set gfxpayload=1280x1024x24, 1280x1024 before linux command instead.**
 
I know my resolution dont go that high and is set to 1280x800 if this helps!
 
How do I fix with LiveCD I see no options for restore when it boots up????
 
Thanks

---

### Post by Muscovy on 2010-02-22
To boot a LiveCD, put one in the drive, then reboot the computer, and you will boot into a "live" environment; a slower, temporary one. You can fix the problem by editing a file, or running a command, but I'm afraid I don't know what. :|

---

### Post by robembra on 2010-02-22
Thanks for the information so I want to choose boot from cd. I have googled it but i have had no look....any help grateful.

Thanks

---

### Post by plucky on 2010-02-23
> **robembra said:**
> Thanks for the information so I want to choose boot from cd. I have googled it but i have had no look....any help grateful.

Thanks

Boot to grub screen 
Press "e" key to edit the grub boot command
Add the **gfxpayload=800x600x8** to the line just before **quiet splash**
Press Ctrl X to start the boot sequence.

and see if that fixes the resolution problem.

If it works,it will only be for the one boot attempt as it doesn't change the boot file on the disk.You will have to use startup manager to change it down to a resolution that will work.

Good Luck

---

### Post by robembra on 2010-02-27
Thanks for the reply it worked a treat.

---

