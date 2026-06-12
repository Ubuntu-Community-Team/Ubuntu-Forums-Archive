---
title: "Re-installing GRUB"
date: 2009-09-11
forum: General Help
---

### Post by iEthan on 2009-09-11
I had two partitions: Vista and Ubuntu. I installed XP over Vista and, unwittingly, I uninstalled GRUB.

I cannot get into Ubuntu. How do I install GRUB from XP?

---

### Post by Sin@Sin-Sacrifice on 2009-09-11
[http://ubuntuforums.org/showthread.php?t=818177&highlight=HOWTO](http://ubuntuforums.org/showthread.php?t=818177&highlight=HOWTO)

---

### Post by lindsay7 on 2009-09-11
Do this,

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)".
Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition
numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or
whatever your hard disk + partition # is, to install GRUB to a
partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

---

### Post by hal10000 on 2009-09-11
Boot your ubuntu live-cd, then post the output of 
[COLOR="Red"]sudo fdisk -l[/COLOR]
Then open the partition where your ubuntu system resists (with your file manager), navigate to the directory [COLOR="Red"]/boot/grub[/COLOR] and post the content of the file menu.lst.

---

### Post by iEthan on 2009-09-12
I fixed it with that first thread. Thanks everyone!

---

