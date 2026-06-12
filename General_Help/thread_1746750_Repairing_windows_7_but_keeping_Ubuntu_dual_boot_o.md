---
title: "Repairing windows 7 but keeping Ubuntu dual boot option"
date: 2011-05-02
forum: General Help
---

### Post by LandR on 2011-05-02
Hi,

I have a fubar'd Windows 7 install I need to get working on another partition so I can do some development stuff. 

I use Ubuntu 95% of the time though and so the machine has an option at boot for what OS I want to go into.

Does anyone know if I boot up with the Windows disc in and choose the repair option if it will screw up my boot options and I potentially lose my ability to boot into Ubuntu ?

If so, is their anyway to prevent this.

Thanks,

---

### Post by mikewhatever on 2011-05-02
Yes, it will, and you will definitely lose the Ubuntu boot option, but it's easy to bring it back.  Use the Ubuntu installation media to reinstall the boot loader, or alternatively, make a backup of the MBR, and restore from it after repairing W7.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
[http://members.iinet.net.au/~herman546/p6.html#MBR_Backup_and_Restore](http://members.iinet.net.au/~herman546/p6.html#MBR_Backup_and_Restore)

---

