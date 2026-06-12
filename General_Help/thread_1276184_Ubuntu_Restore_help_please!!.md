---
title: "Ubuntu Restore help please!!"
date: 2009-09-26
forum: General Help
---

### Post by xxterry1xx on 2009-09-26
Hello i have vista on 1 harddrive and ubuntu on the other harddrive, i kept getting bsod's,slowness and other stuff with vista so i installed xp and ubuntu doesnt show up and grub doesn't show up i tryed useing easyBCD but it said it requires vista i also got data on the other harddrive(ubuntu) i need i tryed looking for the second harddrive in explorer but its hidden
 
but anyone help please :(

---

### Post by sideaway on 2009-09-26
boot your live CD and then follow

```
# Boot your computer up with Ubuntu CD
# Open a terminal window or switch to a tty.
#

Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
# Type "grub"
# Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
# Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
# Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
# Quit grub by typing "quit".
# Reboot and remove the bootable CD. 
```

---

### Post by xxterry1xx on 2009-09-26
> **sideaway said:**
> boot your live CD and then follow

```
# Boot your computer up with Ubuntu CD
# Open a terminal window or switch to a tty.
#

Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
# Type "grub"
# Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
# Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
# Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
# Quit grub by typing "quit".
# Reboot and remove the bootable CD. 
``` Thanks i got the backup folder so i guess ill reinstall ubuntu cause the thing aint working but i got my backups

---

