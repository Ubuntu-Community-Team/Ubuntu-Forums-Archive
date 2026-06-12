---
title: "After installing ubuntu for dual boot, I can't boot to Ubuntu OS"
date: 2009-12-10
forum: General Help
---

### Post by meazz1 on 2009-12-10
I installed Ubuntu 9.10 in a laptop, which already had windows 7 installed. I chose the default option to install Ubuntu side by side of windows. 
Only thing I changed in the Advance option is to tell where the boot loader would be installed. I chose sda3 instead of hd0.
When I restart, the pc boots into windows. I do not see any grub or boot loader option. So I can’t go into Ubuntu.

How can I reinstall grub?

---

### Post by oldfred on 2009-12-10
Computers boot from the drive selected in the BIOS by looking in the MBR for further instructions. Since you did not overwrite the windows boot loader you still boot windows. The install of grub to the partition only is for advanced users with multiple installs using chainbooting.

If you did a clean install you should have grub2, so be sure to follow grub2 instructions. If it was an upgrade you probably have grub legacy. Do not mix old grub and grub2 instructions.
Several versions all the same but worded a little different:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

This has instructions for both old and new:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by oldfred on 2009-12-10
You seem to have two entries in general help? We prefer only one so if our suggestions are not quite right someone else will correct us. If there are two threads you may get different answers without others seeing the first. Also we are all volunteering our time so we may waste time creating duplicate answers in the other thread.

See
[http://ubuntuforums.org/showthread.php?t=1351186](http://ubuntuforums.org/showthread.php?t=1351186)

---

### Post by meazz1 on 2009-12-10
> **oldfred said:**
> You seem to have two entries in general help? We prefer only one so if our suggestions are not quite right someone else will correct us. If there are two threads you may get different answers without others seeing the first. Also we are all volunteering our time so we may waste time creating duplicate answers in the other thread.

See
[http://ubuntuforums.org/showthread.php?t=1351186](http://ubuntuforums.org/showthread.php?t=1351186)

sorry, it was not intentional. Window locked up and I did not know if it was posted.

---

### Post by meazz1 on 2009-12-11
> **oldfred said:**
> Computers boot from the drive selected in the BIOS by looking in the MBR for further instructions. Since you did not overwrite the windows boot loader you still boot windows. The install of grub to the partition only is for advanced users with multiple installs using chainbooting.

If you did a clean install you should have grub2, so be sure to follow grub2 instructions. If it was an upgrade you probably have grub legacy. Do not mix old grub and grub2 instructions.
Several versions all the same but worded a little different:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

This has instructions for both old and new:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) 
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Thank you for your input. I was able to resolve my issue by following one of the link you provided.

---

