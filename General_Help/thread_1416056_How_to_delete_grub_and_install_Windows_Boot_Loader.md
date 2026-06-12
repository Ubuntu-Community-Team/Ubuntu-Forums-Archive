---
title: "How to delete grub and install Windows Boot Loader?"
date: 2010-02-25
forum: General Help
---

### Post by okayneil on 2010-02-25
Hey guys, 

I bought a new laptop and want to give my other one over to my wife with just windows on it. 

I am currently dual booting Windows 7 and Ubuntu 9.10. Windows was installed first. 

I want to delete the ubuntu install in its partition and the let the wife us it as a Music partition so i need to reinstall windows bootloader as deleting the partion with cause grub to be deleted. 

Any ideas on how to do this?

---

### Post by NefariousNobo on 2010-02-25
What you probably would want to do is boot into Windows 7. Download and install EasyBCD ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)) unless you prefer to use Windows 7's command-line bcdedit.exe (I never figured that one out myself). When you run EasyBCD, it should detect the absence of the NT 6 Kernel's bootloader, and ask if you would like it to restore it. With any luck, telling it you would should have it rewrite the MBR. Alternatively, you could boot from the Windows 7 installation (or reinstallation) disk and rewrite the MBR from there.

---

### Post by okayneil on 2010-02-25
Could I not just delete the partition (which deletes grub) and then use the recovery cd for windows?

---

### Post by philinux on 2010-02-25
Easybcd works a treat.

---

