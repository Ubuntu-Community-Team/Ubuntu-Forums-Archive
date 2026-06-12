---
title: "Another wubi rot.disk problem..."
date: 2010-01-01
forum: General Help
---

### Post by DeathRabbit on 2010-01-01
Hi all, my bro is running Wubi as well and just today it started dropping him to intrafmfs saying that root.disk was missing or some such nonsense. I say nonsense because I booted into Windows and it was still there in the Ubuntu folder where it was supposed to be. Is there any way to fix this? Thanks.

---

### Post by drs305 on 2010-01-01
Is the first menu controlled by Windows? Is that where the problem occurs?

Does he get to a Grub-created menu and is it Grub 2?

If he is using Grub 2 (Karmic) and if he can get to a menu controlled by Grub 2, he can press "e" to edit the menu entry or he might be able to drop to the grub command line and use the "ls (hdX,Y)/boot" command to see if the boot files are there.

These options are included in the community doc: 
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

Note if entering the linux line via the grub command line there is a specific addition for wubi. It's included in the guide.

---

