---
title: "dual boot problems"
date: 2011-08-23
forum: General Help
---

### Post by physicsisfeyn on 2011-08-23
When I switch from my windows partition to the ubuntu partition, ubuntu fails to boot and shows a black screen. I have to power of the computer to get ubuntu to boot.

I'm using the ubuntu boot manager.

---

### Post by oldfred on 2011-08-23
Welcome to the forums.

Is this a wubi install inside windows or a full install to partitions. 
Do you get a grub menu? 
If you have a grub menu then it may be video related. 
What video card?

If video, these may help:
Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by physicsisfeyn on 2011-08-23
It is a full install to partitions. I have a grub menu. 
The video card is a GeForce Gt 540M
Could optimus be causing the problem? I only receive the black screen after the first time I boot after restarting the computer from the windows partition. It never occurs any other time.

Also on a somewhat related note, has ubuntu found a solution to the optimus problem? I currently have the video card turned off in ubuntu.

---

### Post by oldfred on 2011-08-23
It is not Ubuntu but nVidia. They have said they will not support Optimus in Linux driver. But that may change.

Update says there may be some hope.
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

