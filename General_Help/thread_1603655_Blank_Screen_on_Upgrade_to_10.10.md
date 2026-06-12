---
title: "Blank Screen on Upgrade to 10.10"
date: 2010-10-23
forum: General Help
---

### Post by GigaRoc on 2010-10-23
I have an HP 2730p
After upgrade i have a blank screen.  i don't get a splash screen and i can't alt+ctrl+F6 to get extra terminal.

Unfortunately i can't ssh into the box either since i don't have openssh-server installed.

Is there anything i can do short of taking the harddrive out and putting it into another box?


Kevin A

---

### Post by LPopov on 2010-10-25
I have the same problem. When the laptop is booting hold the shift key and grub menu should open. See if you have 2.6.32 kernel installed and if you do - boot it.
See also [http://ubuntuforums.org/showthread.php?t=1592763](http://ubuntuforums.org/showthread.php?t=1592763) .

---

### Post by Ampi on 2010-10-25
I haven't had exactly the same problem, but yesterday when I installed Ubuntu Netbook on a laptop, I had a blinking white screen and couldnt see anything behind that screen. Apparently that was a problem with the graphics card that could handle Unity which is part of the Netbook Edition. 
Maybe it can help..

---

