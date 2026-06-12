---
title: "Grub2 settings not retained - reinstall grub?"
date: 2010-08-14
forum: General Help
---

### Post by tgeer43 on 2010-08-14
This is closely related to a recent thread of mine that I unfortunately marked as solved prematurely. I'll try to keep it brief this time.

After editing partitions I was left with a boot problem, namely "error: no such partition" and I am dropped at the 'grub rescue>' prompt. I can issue the appropriate grub commands and successfully boot the current kernel. Once booted, I executed 'sudo update-grub' and then /boot/grub/grub.cfg was rewritten with all drive and partition references correct. Likewise, /etc/fstab is also correct.

The problem comes when I attempt to reboot. I still get the 'no such partition' message and the 'set' command reveals that grub is still trying to reference the old partition. I've never encountered this problem before under similar circumstances.

I'm guessing that this info must be stored in the disk's MBR as well as in grub.cfg because that file looks completely correct. Am I going to have to reinstall grub now?

I *really* need your help folks. For now I'm severely limiting my reboots to avoid having to issue all of those grub commands each time. Thanks in advance.

Regards,

tgeer

p.s. I can provide much more detail if needed or you can refer to my earlier thread here: 
[COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1552785](http://ubuntuforums.org/showthread.php?t=1552785)[/COLOR]

---

### Post by yabbadabbadont on 2010-08-14
If you edited partitions then you will have to reinstall grub.  Since you can get the system to boot, it is pretty easy to do.  Just use the grub-install command.  ("man grub-install" for details)

---

### Post by tgeer43 on 2010-08-18
Yeah, I finally did that but still don't understand why in the past I've been able to boot using grub rescue commands and then execute 'sudo update-grub' to set things straight but this time updating grub did not resolve the issue.

Ah well, on to bigger and more pressing matters. Thanks for taking time to reply.

Regards,

tgeer

---

### Post by oldfred on 2010-08-18
You have to reinstall grub2 to the MBR.

While in the LiveCD, open terminal and run:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

OR if booted into your system and want it in sda:

sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda

---

