---
title: "grub rescue"
date: 2009-11-27
forum: General Help
---

### Post by cendo1 on 2009-11-27
This is an embarassing question. My puter has Vista Ultimate with 600 gb disk.
I was going to install Kubuntu on my old XP puter. Since I have a large storage on my new computer, I installed Kubuntu 9.1 on my Vista puter which downloaded the K Os without any problem. K OS partitioned my disk. Eventhough I deleted K OS, it stayed on as the primary OS. Then I went to Administration-storage where I deleted the the partition where I thought K OS was. Now when I reboot the puter, grub rescue comes out, and I can not bring out the VISTA OS. Can anyone help me how to bring back VISTA OS, and eliminate the partitioned drive where I asume Kubuntu OS was?

---

### Post by oldfred on 2009-11-27
Your install put grub into the MBR and when you erased Kubuntu you erased all the files the grub in the MBR pointed to.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Uninstall Ubuntu and fix windows boot:
[http://ubuntuforums.org/showpost.php?p=7526905&postcount=4](http://ubuntuforums.org/showpost.php?p=7526905&postcount=4)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc  for repairs only at the following links:
Windows Vista/7 Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by cendo1 on 2009-11-30
Thank you for your reply. But I do not know how to do it.
 
When I try to boot the puter, the followings come out
PCI Devices Listing....
(some listings)
Verifying DMI Pool Data.....
GRUB loading.
error: no such partition
grub rescue> _ (prompt)
 
I tried what you said, but nothing works.
What shall I do? Can you or anyone fix this problem?
I will be happy to pay for fixing.

---

### Post by oldfred on 2009-11-30
My first link has how to repair Vista and Win7 which are basically the same. My other links will take you to a site to download a repair disk if your windows/hardware OEM vendor did not give you a full disk. The download disk is only to boot and repair. 

They prefer we link to sites for many standard repairs as they are often more complete. Occasionally we may need to customize and that can lead to troubles for others trying to use the same commands.

from with better explanation of the steps to start disk to get to the repair your disk screen and in command prompt type:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

type in:
bootrec.exe /fixboot
bootrec.exe /fixmbr

This will replace grub in the MBR, and repair other parts of windows that may need fixing. The second command probably is all that is required to replace grub.

We are all volunteers here and just are just trying to help promote Ubuntu.;)

---

