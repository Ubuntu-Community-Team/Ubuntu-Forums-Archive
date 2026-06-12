---
title: "Should I try editing grub.cfg manually?"
date: 2012-05-29
forum: General Help
---

### Post by linuxgod on 2012-05-29
Hi all,

I want to change the grub timeout to more than 1 second, because "1 second" is more like 1 microsecond and I'm currently not able to boot into Linux ...

I'm about to modify /boot/grub/grub.cfg manually:

change timeout=1 to timeout=5

from within Windows 7 using Ext2Fsd. But grub.cfg has a comment clearly stating that you should not edit this file ... so thought I'd ask here before proceeding.

Thanks!
S

PS I also want to avoid using the Ubuntu CD ...

---

### Post by deadflowr on 2012-05-29
You'll want to edit the /etc/default/grub file, editing the grub.cfg file can mess up your system, and will revert back whenever any update-grub is run. Read the above mentioned file carefully.

---

### Post by linuxgod on 2012-05-29
> **deadflowr said:**
> You'll want to edit the /etc/default/grub file, editing the grub.cfg file can mess up your system, and will revert back whenever any update-grub is run. Read the above mentioned file carefully.

Thanks. Do you think update-grub is run at boot time? As I'm editing from Windows, I can't run update-grub after I edit /etc/default/grub

---

### Post by oldfred on 2012-05-29
While you should never edit grub.cfg, you can in an emergency.  Understand any edits will be overwritten on sudo update-grub.

I would not use any Windows tools to edit grub.cfg. You may destroy file as Windows uses different line endings. Even spaces at end can cause problems.

grub.cfg is read only and should not normally be edited, change sda5 to your partition:

mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or one of these first:
sudo chmod 777 /mnt/boot/grub/grub.cfg
sudo chattr -i /mnt/boot/grub/grub.cfg
gksu nano +28 /mnt/boot/grub/grub.cfg

sudo nano /mnt/boot/grub/grub.cfg

Linux, of course, uses only LF as newline and DOS is expecting CR/LF.

---

### Post by sisco311 on 2012-05-29
EDIT: ninja'd by oldfred :)

In theory, it should work, but editing the file manually is not recommended for many reasons. For example, Windows uses CR-LF pairs for line endings, while Unix/Linux uses LFs only. So, you will have to make sure that your text editor in Windows saves the file in Unix/Linux format. That's only one issue you might encounter. And, even if you edit the file in Windows, you will still need to edit /etc/default/grub and run update-grub in Ubuntu.
 
If you hold down the Shift key during the boot process, then the boot menu will show up. You will be able to boot into Ubuntu and make the desired changes, in the proper way, from there.

---

### Post by linuxgod on 2012-05-30
Thanks!

Using the live CD, I mounted the boot partition, changed the grub.cfg permissions and edited the file setting timeout=5, as outlined by oldfred. It worked! Once booted into linux, I configured grub properly, editing /etc/default/grub and running update-grub.

These threads contain the solution: [http://ubuntuforums.org/showthread.php?t=1650021](http://ubuntuforums.org/showthread.php?t=1650021) and [http://ubuntuforums.org/showthread.php?t=1567456](http://ubuntuforums.org/showthread.php?t=1567456)

> **sisco311 said:**
> EDIT: ninja'd by oldfred :)
 
If you hold down the Shift key during the boot process, then the boot  menu will show up. You will be able to boot into Ubuntu and make the  desired changes, in the proper way, from there.
I wish I'd known this before!

PS I am aware of the different encodings in Windows and Linux and could have probably handled editing from Windows, but in the end got too scared and used the live CD. :)

Cheers,
S

---

