---
title: "Huge problem with GRUB"
date: 2010-08-10
forum: General Help
---

### Post by anewa on 2010-08-10
I need some _serious_ help! I have an Acer netbook and I recently formatted the partition that had ubuntu netbook remix using the disk managment tool on windows XP foolishly thinking it would just clear ubuntu but I totally forgot about the GRUB, now I'm trying to access windows again but I just cant. Everytime I try to boot the PC it only shows the message "error: no such partition" and then it displays grub rescue>
I've tried booting from a pendrive using the linux iso, the windows xp iso and using puppy linux iso but it always says boot error and wont do anything else.
I need help urgently because I constantly use this laptop and I just cant afford something else.

---

### Post by dcstar on 2010-08-11
> **anewa said:**
> I need some _serious_ help! I have an Acer netbook and I recently formatted the partition that had ubuntu netbook remix using the disk managment tool on windows XP foolishly thinking it would just clear ubuntu but I totally forgot about the GRUB, now I'm trying to access windows again but I just cant. Everytime I try to boot the PC it only shows the message "error: no such partition" and then it displays grub rescue>
I've tried booting from a pendrive using the linux iso, the windows xp iso and using puppy linux iso but it always says boot error and wont do anything else.
I need help urgently because I constantly use this laptop and I just cant afford something else.

You have to reinstall the Windows bootloader, there are already hundreds (probably thousands) of posts on the Internet on how to do this.

---

### Post by Fludizz on 2010-08-11
Quickest solution is to boot using a bootable DOS disk (USB, Floppy) and issue fdisk /mbr. This should clear your Master Boot Record in which the GRUB reference is located. With a clean MBR windows should boot as windows doesn't use the MBR but relies on the BOOTABLE flag on the partition in which its bootfiles reside.

Another way is to boot the Windows XP install CD and open te recovery console. That console has some commands to fix boot issues (amongst others to clear the MBR).

---

### Post by varunendra on 2010-08-12
If you can get a USB cd drive (assuming your netbook doesn't have an optical drive) then boot off XP installation cd, hit 'R' (for recovery) at the first prompt and supply your Administrator password (if any) when prompted.

Then at the command prompt type- **fixmbr**. Then reboot and your XP will be back.

Another alternative (if you can't get a USB cd drive): If you can find a laptop whose hard disk's connection interface is same as yours, then hook your hard disk to that one and proceed to steps told above. (instead of reboot, poweroff > replace the HDD to the netbook then boot)

If you need to reinstall XP without CD, follow [this]("http://ubuntuforums.org/showthread.php?p=9190079") (It's my own experience) or post #13 by oldfred on the same page.

---

