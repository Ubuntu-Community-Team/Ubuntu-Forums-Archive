---
title: "Partition becomes invalid after VirtualBox installation"
date: 2011-11-16
forum: General Help
---

### Post by jampe on 2011-11-16
Windows 7 screwed me over for the last time, so I'm switching my gaming OS back to XP :) I am able to install Windows XP x64 on a physical partition via VirtualBox using the raw disk image method:
```

VBoxManage internalcommands createrawvmdk -filename /home/<USERNAME>/.VirtualBox/WinXP.vmdk -rawdisk /dev/sdaX -relative

```

It installs and runs in VirtualBox without any hiccups, I can see that the C drive has the same size as the assigned partition (/dev/sdaX) and such.

**But, but, but..**
Now the partition turns up as "unknown" in Disk Utility, and GRUB is unable to identify it upon executing update-grub. Needless to say, I'm unable to boot into my new WinXP installation.

I get a BSOD when trying to install it from CD, so I really need this to work. Have I somehow gotten this all wrong?

BTW, I'm not using 10.04, I'm on 11.10, but the questionable forum policy won't allow me to change it before I've written 50 posts :P

---

