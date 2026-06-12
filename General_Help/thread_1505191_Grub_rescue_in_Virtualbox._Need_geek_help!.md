---
title: "Grub rescue in Virtualbox. Need geek help!"
date: 2010-06-08
forum: General Help
---

### Post by schwabdale on 2010-06-08
I am dual booting a pc with Ubuntu and Windows 7. I am using Grub as the boot loader. I then boot into Windows 7 and Create a virtual hard drive (.vhd) file using Disk2Vhd. 
After the machine is converted, I boot into Ubuntu, and import the .vhd into Virtualbox. 

Problem:
When I turn on the virtual machine in Virtualbox, It comes up with Grub rescue. How do 
install Grub to the virtual machine. 

I can boot the virtual machine in virtualbox off of a Ubuntu CD, and then somehow install Grub....Maybe... I'm not sure what to do. Any help would be appriciated.

---

### Post by quixote on 2010-06-09
The fact that grub rescue comes up implies grub is installed.  It's just having trouble figuring out where the bootable OSes are.  Try booting into virtualbox, and when the grub rescue comes up, try following the regular instructions (eg [here]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")) and see whether that solves the problem.

---

