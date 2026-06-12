---
title: "Startup Error"
date: 2010-12-31
forum: General Help
---

### Post by MightyM3 on 2010-12-31
I'm using Ubuntu 10.10 and I recently moved my home folder to another hard drive using the psychocats guide. 

After following the instruction, I restarted my computer and was met with an error right before one reaches the login screen. The error message had ubuntu written at the top and beneath it were 4 dots. The message read along the lines of :"Serious errors have been found on _______, unable to mount home". It then gave three options: Ignore, Manual Recovery, and continue without mounting. I entered manual recovery mode and followed the instructions given in the guide (which can be found at [http://www.psychocats.net/ubuntu/separatehome)]("http://www.psychocats.net/ubuntu/separatehome")
After following the instructions given, I was still met with the error. However, upon ignoring the error when face with the message, my computer continued to boot up and function normally.
I've been driving myself insane over this and any help would be greatly appreciated.

---

### Post by Brandon Williams on 2010-12-31
Double check to ensure that there is no conflict between your /etc/fstab file and your new partition layout.

Use 'grep /home /etc/fstab' to figure out how the home partition is listed. Is the first token UUID=... or /dev/...? If it's /dev/..., does it specify the correct device file for the partition? If it's a UUID, use 'sudo blkid /dev/...' to determine the correct UUID, where '...' is the correct device name for your home partition.

If /etc/fstab appears to agree with the partition config and your home directory is correctly mounted by the time you log in, then maybe the error is coming from your initramfs and not from the runtime setup. Did you regenerate your initramfs after changing the partition layout and home directory? Try running 'sudo update-initramfs'.

---

### Post by MightyM3 on 2010-12-31
I did everything you said and it appears as though everything is in order. The directories are consistent and the mount point for home is correct. I also tried your last suggestion, but it did not work properly. After entering sudo update-initramfs, the terminal just gave me the proper usage of initramfs. Can you expand upon how to use the command.

---

### Post by MightyM3 on 2011-01-01
-bump-

Any help on the matter would be greatly appreciated. I still receive the error, yet my system functions perfectly.

---

### Post by Brandon Williams on 2011-01-02
> **MightyM3 said:**
> After entering sudo update-initramfs, the terminal just gave me the proper usage of initramfs. Can you expand upon how to use the command.

Oops, sorry, I forgot that it requires a flag. The man page reminded me that the correct usage in this case is 'sudo update-initramfs -u'.

---

### Post by MightyM3 on 2011-01-05
I updated the initramfs and I'm still receiving the error. Any other ideas as to how to correct this issue?

---

