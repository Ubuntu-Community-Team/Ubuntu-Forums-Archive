---
title: "I got stuck in memory check and can't get out"
date: 2010-11-16
forum: General Help
---

### Post by davedaveh on 2010-11-16
I am in Ubuntu 10.10, working out some issues. I wanted to be able to boot to a command prompt instead of GUI, and used GUI startup option interface to investigate my boot options.  Did not see 'Boot to command line" option, so tried booting to Memory test, thinking I might get a prompt afterwards.  
Now I cannot boot to Ubuntu at all.  This installation is not dual boot.
I have my live install CD in now, but do not know which file to edit to change back this boot option.
Thanks for help.
This is either funny or stupid or both!

---

### Post by wojox on 2010-11-16
Memory tests take a long time. I don't remember seeing a Boot to command line. Just a Drop to root shell.

---

### Post by efflandt on 2010-11-16
Any (recovery) grub menu entries can boot to a text console login (or root console).  It sounds like you booted to memtest86+ which is a text based memory test, but has no login.  Your choices to exit from that are to reboot or manually power down your computer.

Did you alter anything regarding grub to get into memtest86+.  If not and you do not see the grub menu when you boot, try holding the Shift key during your BIOS splash screen and continue to hold it after that (which should bring up the grub menu).

If you changed something related to grub, like grub.cfg, boot a live/install CD or USB and change it back.  Or if you altered something else in /etc/default/grub, you may need to see [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and follow METHOD 3 - CHROOT to update-grub after changing that back (you can probably skip steps 9 & 10).

---

### Post by davedaveh on 2010-11-16
Thanks -- I didn't know about the *shift* option.  It is booting now and I can change the *startupmanager* options easily now.
But how do I boot to a prompt?
It is a single Linux install on this computer. 
The reason I think I need a prompt is because I am installing a video driver. NVIDIA-Linux-x86-96.43.19-pkg1.run
How do I execute that?

Oh -- gdm stop  

No that made it hang

I tried recovery mode -- root shell prompt, but got message I was in the wrong init level....

---

