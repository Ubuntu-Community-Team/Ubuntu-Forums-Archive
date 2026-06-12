---
title: "Uninstalling Ubuntu 12.04 (dual-boot) in order to re-install..."
date: 2012-09-28
forum: General Help
---

### Post by Eirreann on 2012-09-28
Okay, so I followed this tutorial ([http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/")) to dual-boot Ubuntu 12.04.  Everything went great, however I've got this issue (details here: [http://ubuntuforums.org/showthread.php?t=2063704]("http://ubuntuforums.org/showthread.php?t=2063704")) and I'm having the worst of luck finding a fix.  So, I was just going to uninstall Ubuntu and reinstall it the same way.  So, if I just deleted all of the Ubuntu partitions from the Windows Disk Manager, would I be good to go and be able to reinstall it?  Through the tutorial I took, it doesn't seem like the boot loader has been taken over by GRUB2, so I should still be able to access Windows 7 after I've removed those partitions, right?
Can anyone confirm or deny this?

---

### Post by Mark Phelps on 2012-09-28
IF you're installing these on the same physical drive, the one containing Win7, BEFORE you do anything else, do yourself a favor, boot into Win7, and use the Backup feature to create and burn a Win7 Repair CD.  This will give you a way to restore the Win7 boot if anything happens during the Ubuntu removal.

---

### Post by Eirreann on 2012-09-28
> **Mark Phelps said:**
> IF you're installing these on the same physical drive, the one containing Win7, BEFORE you do anything else, do yourself a favor, boot into Win7, and use the Backup feature to create and burn a Win7 Repair CD.  This will give you a way to restore the Win7 boot if anything happens during the Ubuntu removal.

I still have the original Windows 7 install CD, would that work too?  (I don't have any blank disks at the moment...)

---

### Post by ajgreeny on 2012-09-28
I agree that it is worth making the repair disk for windows if you can; it will probably be easier to use than a complete reinstall of Windows.

For the Ubuntu reinstall there is no need to uninstall the current version first; just choose "Something Else" at the disk preparation stage (ie partitioning) and point to the current Ubuntu partitions, /,  and possibly /home.  Ignore the swap as it will be found and used automatically.  The partitions will then be overwritten by the new installation and you should be good to go.

---

### Post by Eirreann on 2012-09-28
> **ajgreeny said:**
> I agree that it is worth making the repair disk for windows if you can; it will probably be easier to use than a complete reinstall of Windows.

For the Ubuntu reinstall there is no need to uninstall the current version first; just choose "Something Else" at the disk preparation stage (ie partitioning) and point to the current Ubuntu partitions, /,  and possibly /home.  Ignore the swap as it will be found and used automatically.  The partitions will then be overwritten by the new installation and you should be good to go.
Ah, well there we go!  (although I don't have a swap partition...)

---

### Post by Eirreann on 2012-09-28
So will the original Windows 7 install CD serve the same purpose as the repair disk??

---

### Post by ajgreeny on 2012-09-29
> **Eirreann said:**
> So will the original Windows 7 install CD serve the same purpose as the repair disk??
No idea;  I do not have windows at all.

---

