---
title: "Grub Error 17"
date: 2009-12-29
forum: General Help
---

### Post by llewdyn on 2009-12-29
I needed space on my HD so I deleted the partition that I had installed ubuntu on and the extra partition that it required. I assumed it would also remove the GRUB utility with it since it was added when I installed Ubuntu. Wrong! Now after loading BIOS all i receive is Grub error 17. I know that means there was an error reading my bootable partitions, but how do I change this without access to command line or being able to boot. Unfortunately I don't have a Windows/recovery disc, but I have another computer that I can plug the HD into to access it, just not boot from it. Thanks for any replies!

---

### Post by staf0048 on 2009-12-29
> **llewdyn said:**
> I needed space on my HD so I deleted the partition that I had installed ubuntu on and the extra partition that it required. I assumed it would also remove the GRUB utility with it since it was added when I installed Ubuntu. Wrong! Now after loading BIOS all i receive is Grub error 17. I know that means there was an error reading my bootable partitions, but how do I change this without access to command line or being able to boot. Unfortunately I don't have a Windows/recovery disc, but I have another computer that I can plug the HD into to access it, just not boot from it. Thanks for any replies!

Hmm, this question might be better off on a Windows forum, but if I were you I'd search google for a windows recovery disk.  Depending on your version, xp/vista/7 etc, you need to run a program called fixmbr, fixboot, or something like that.  That will replace Grub with the windows mbr.

---

### Post by synapsys on 2009-12-29
It really does depend which version of windows you're using....

Here's a tutorial for vista

[http://swanbros.blogspot.com/2009/01/how-to-repair-windows-vista-bootloader.html](http://swanbros.blogspot.com/2009/01/how-to-repair-windows-vista-bootloader.html)

---

### Post by llewdyn on 2009-12-29
Sorry I'm running XP.

---

### Post by corn3lius on 2009-12-29
Try using the Super Grub tool kit cd. It is a life saver.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

