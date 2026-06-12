---
title: "Ubuntu Missing!!!"
date: 2010-12-22
forum: General Help
---

### Post by delonicdevil on 2010-12-22
Hi people, 

Ok here is what happened. 

I had a laptop that dual boots Xp and Ubuntu. 

Something went wrong with the Xp. So I recovered it using my recovery partition for my Xp. 

Afterwhich, my Ubuntu was gone. I was no longer able to select which OS i would like to boot as before.

Can anyone help me?

---

### Post by 3Miro on 2010-12-22
Windows is a bully and doesn't play nice with other operating systems. At he very least, it flushed the master boot record, so you can no longer boot into Ubuntu. It is possible that Ubuntu was flushed altogether.

Get a Ubuntu live CD and boot form there (it is best for the CD to be the same version as the Ubuntu installed). Then look at your partitions to make sure Ubuntu is still there. If Ubuntu's partitions are still there, you will simply need to reinstall Grub (the Ubuntu boot manager). This is the official HowTo:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

You need section 12: Reinstalling GRUB 2.

---

### Post by coffeecat on 2010-12-22
There are two possible things (that I can think of offhand) that may have happened:

1 - your XP recovery rewrote the Windows MBR and restored a factory default XP to the C: drive but left the Ubuntu partitions alone. In which case it will be simple to repair grub to get you booting into Ubuntu again.

2 - your XP recovery partition has rewritten your hard drive back to factory default, but used the whole drive. In which case you will have lost Ubuntu.

To see which has happened, boot up a live Ubuntu CD or live Ubuntu USB. Go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file. Please remember to enclose the output in code tags - you can use the # icon in the message toolbar.

---

