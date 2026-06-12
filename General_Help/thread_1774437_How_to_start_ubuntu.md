---
title: "How to start ubuntu"
date: 2011-06-03
forum: General Help
---

### Post by shiva28 on 2011-06-03
I have installed Ubuntu from the USB, everything fine after the installation, he asked me to restart the PC.
I restarted it, but then it doesn't give me the possibility to choose between the OS that I have installed, and it runs always windows..

how can I solve this? 

Thank you ;)

---

### Post by aphatak on 2011-06-03
Did you install the Wubi version?  If you did, you will get Windows, and then you will have to start Ubuntu from within Windows.
Can you see the partitions into which you installed Ubuntu (in Disk Management app)?
If you installed the desktop version, did you install Grub2 in the MBR?  If you did not, you could -
[LIST=1]
[*]Install Ubuntu again, making sure Grub2 goes into MBR
[*]Boot with the SuperGrub live CD (which you will have to download and burn if you haven't already), and then install Grub2 from it.
[/LIST]
If you need detailed steps, post a reply to this and you and I can figure the problem out.

---

### Post by shiva28 on 2011-06-03
> **aphatak said:**
> Did you install the Wubi version?  If you did, you will get Windows, and then you will have to start Ubuntu from within Windows.
Can you see the partitions into which you installed Ubuntu (in Disk Management app)?
If you installed the desktop version, did you install Grub2 in the MBR?  If you did not, you could -
[LIST=1]
[*]Install Ubuntu again, making sure Grub2 goes into MBR
[*]Boot with the SuperGrub live CD (which you will have to download and burn if you haven't already), and then install Grub2 from it.
[/LIST]
If you need detailed steps, post a reply to this and you and I can figure the problem out.


I install it from the USB, not with wubi. I downloaded the last version from the website and I made the startup USB desktop version with another PC (by using Ubuntu).
How can I install Grub2? I didn't see it during the installation, It just let me chose the partition size and the languages (keyboard and OS), nothin else.

---

### Post by linuxinstalledfromhdd on 2011-06-03
You can try this..  I don't know it if it will help though.. You are going to need to boot from your live disc.

[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

---

### Post by ajgreeny on 2011-06-03
I suggest you run your live USB version of ubuntu, and from that download and follow the instructions on the **Boot-info-script** link in my signature, copying the RESULTS.txt file back here in code tags (the # above, in the text entry box).  WE weill then be able to see how the install went and where grub is installed, etc, etc.

---

