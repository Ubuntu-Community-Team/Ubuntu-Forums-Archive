---
title: "Dual boot setup question"
date: 2006-04-03
forum: General Help
---

### Post by kudu on 2006-04-03
I have two HDs, the master has the MBR and Windows on it, and the slave has Ubuntu Breezy. My default OS is Ubuntu Breezy. How do I uninstall Windows from HDA without terminating the MBR and messing everything up ??

---

### Post by aysiu on 2006-04-03
Do you really want to uninstall Windows or just take Windows off the MBR and put Ubuntu's Grub there instead?

---

### Post by kudu on 2006-04-03
Don't need it on this particular machine. I now have two PC towers connected to single monitor, keyboard, mouse setup using a KVM switch. It's really cool. Hit a hotkey and I'm in windows, hit it again and I'm back in ubuntu. Very cool!

I have two HD's on my Linux machine though and was wondering how I would remove windows without messing up my perfectly good ubuntu setup. No emergency, but one never knows.

---

### Post by aysiu on 2006-04-03
Best way to remove Windows:

1: Unmount it (*sudo umount /dev/hda1* most likely)
2: Reinstall Grub: [https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)
3: Reformat it as Ext3 (using GParted)
4: Add an appropriate entry to your /etc/fstab

Let me know if you need help with #1 or #4.

---

