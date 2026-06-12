---
title: "Allocating more hard drive space?"
date: 2010-07-13
forum: General Help
---

### Post by Swift101 on 2010-07-13
[FONT="Arial"]Hi all,

I have recently install Ubuntu to run along side Windows. I gave Ubuntu 17 Gbs, which is fine, but would it be possible to give Ubuntu some more hard drive space without having to reinstall the entire OS?

-Thanks[/FONT]

---

### Post by gsgleason on 2010-07-13
Yes.

boot to any live distro that has the gnome partition editor (gparted).  It will let you resize partitions and filesystems with a nice gui interface.

---

### Post by Mark Phelps on 2010-07-13
> **Swift101 said:**
> [FONT="Arial"]Hi all,

I have recently install Ubuntu to run along side Windows. I gave Ubuntu 17 Gbs, which is fine, but would it be possible to give Ubuntu some more hard drive space without having to reinstall the entire OS?

-Thanks[/FONT]
If your disk is full, you're going to have to shrink the MS Windows partition to grow the Linux filesystem.  If your Windows version is Vista or Win7, do NOT use GParted to do the shrinking.  Instead, use the Vista/Win7 Disk Management utility to shrink the Windows partition.  Then reboot into Vista/Win7 before you do anything else to allow it to reset the filesystem.

Only after you have done that should you then resize the Linux filesystem.

---

### Post by Swift101 on 2010-07-13
Thanks, I tried that but I installed Ubuntu on my Windows partition without creating a separate  partition just for Ubuntu.Is there anyway I could still give it some more room? (I'm sorry if I'm not catching on right away I'm new to Linux/Ubuntu)

---

### Post by xenosaga456 on 2010-07-13
did u use wubi? if so then just go to windows and reinstall it with a diffrent size

---

### Post by Swift101 on 2010-07-13
> **xenosaga456 said:**
> did u use wubi? if so then just go to windows and reinstall it with a diffrent size

Yeah I did, so I guess that would be my only option right?

---

### Post by xenosaga456 on 2010-07-15
no you can start ubuntu before the computer boots and install it there it will automatically ask u what size to resize windows just slide the bar to the GB u whant
1st. uninstall wubi....and backup all of ur ubuntu files

2nd. put the .iso u burned into the cd drive then restart the computer from there ubuntu will come up select ur language then select install ubuntu and follow the on screen instructions

---

