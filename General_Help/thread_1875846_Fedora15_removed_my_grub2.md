---
title: "Fedora15 removed my grub2"
date: 2011-11-05
forum: General Help
---

### Post by deff182 on 2011-11-05
Hi guys, recently i've decided to try Fedora15 due to Ubuntu's interface issues. before installing i had two hard drives (master(ubuntu+storage), slave(windows+junk)). 
On master hard drive with Ubuntu i had grub2, after installing Fedora in addition to Ubuntu on master hard drive - i only get instant fedora loading. i guess it's because fedora linked master-boot record to its own grub. 
I want to restore grub2 and add a Fedora section to it - is it achievable? how?
Thanks.

---

### Post by drs305 on 2011-11-05
If you aren't able to boot into an existing Ubuntu installation, boot the Ubuntu LiveCD (same version as the one you want to boot from), then mount the Ubuntu partition and reinstall Grub 2. This will point the MBR back to the Ubuntu boot files. Change X to the proper boot drive (a,b,c, etc) and Y to the correct Ubuntu partition (1,2,3, etc). Don't use the Y value in the second command.

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
sudo umount /dev/sdXY

```

*After* rebooting from the Grub 2 menu, run "sudo update-grub" to see if it picks up the Fedora installation.

Note: Fedora 15 and earlier use Grub Legacy but Fedora 16 finally upgraded to Grub 2.

---

### Post by deff182 on 2011-11-05
:D Thank you, it has worked with one correction to --boot-directory=/mnt/boot/. after that i used "grub-customizer" tool which found Fedora. Great:popcorn:

---

### Post by drs305 on 2011-11-05
> **deff182 said:**
> :D Thank you, it has worked with one correction to --boot-directory=/mnt/boot/. after that i used "grub-customizer" tool which found Fedora. Great:popcorn:

I mixed the old and the new. Prior to Grub 1.99 it was "root-directory=/mnt" and Grub 1.99 is "--boot-directory=/mnt/boot", although the former works too. I usually use the former, but I'm glad you figured it out. I corrected the original should someone happen upon this thread.

If you don't have any other issues you can mark the thread "SOLVED" via the 'Thread Tools" link near the top right of the original post.

Happy Ubuntu-ing !

---

