---
title: "GNU GRUB Error - Nothing will boot!"
date: 2011-07-21
forum: General Help
---

### Post by nouveaucool on 2011-07-21
My boot GRUB is GNU GRUB 1.99.  I dual-boot Ubuntu and Windows.  Earlier today, my computer locked up while running Ubuntu so I restarted, only to find that nothing on my computer would boot past the GRUB.  Not Ubuntu, not Ubuntu in Recovery Mode, not Windows, not Windows Recovery Environment, not Memory Text... well you get the picture.

The error message I receive for Ubuntu reads:
"error: unknown command '['.
error: unknown command '['.
error: unknown command 'save_env'.
error: unknown command 'search'.
error: unknown command 'linux'.
error: unknown command 'initrd'."

For Windows it reads:
"error: unknown command 'search'.
error: unknown command 'chainloader'."

I haven't tried a boot disk because I don't have access to one at the moment (I'm in college, I'd have to go buy blank CDs and burn my own).  In the past I've solved GRUB problems by using a Windows Recovery Disk, but I don't have access to that right now either.  My options are editing the commands or opening a command-line.  Is there anything I can do to solve this problem?

---

### Post by nouveaucool on 2011-07-21
I haven't installed anything lately that should have messed with the GRUB.  Only the latest updates for Ubuntu.

---

### Post by drs305 on 2011-07-21
It looks like Grub is failing at the very first stages. However, if you can get to a "grub rescue" prompt you may be able to boot. Do you ever see the rescue prompt, or can you hold down the SHIFT key during boot to get to the grub menu?

Having a LiveCD would be of great help, but if you can't get one you but can get to a grub prompt you may be able to boot using the procedures in this Grub Rescue thread:
[http://ubuntuforums.org/showthread.php?t=1594052]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by nouveaucool on 2011-07-21
.

---

### Post by nouveaucool on 2011-07-21
I cannot hold down the shift key to get to grub, and I do not see a rescue prompt.  Is a Live CD my only hope?

---

### Post by drs305 on 2011-07-21
> **nouveaucool said:**
> I cannot hold down the shift key to get to grub, and I do not see a rescue prompt.  Is a Live CD my only hope?

CD/DVD/USB Ubuntu or another Linux OS or repair CD. I'm assuming you are posting from a completely separate computer.

The commands you are seeing are the very first lines of the grub configuration file failing to run. The grub rescue prompt allows the user to point to certain grub files/modules, but without getting them loaded you can't run Grub 2. 

If you can use a bootable device (CD, flash drive, etc) to boot you can repair Grub2 using guides on the forum (such as the chroot guide in my signature line) or the 'Boot Repair' app which you can also find linked in the Ubuntu forums. Other options include the Grub Super Disk (rescatux), and it's even possible you just have errors that could be repaired by running an fsck check on the unmounted partition. But for all these options you'll need an external source to boot.

---

### Post by nouveaucool on 2011-07-22
Thank you, I'm trying Rescatux right now.

---

