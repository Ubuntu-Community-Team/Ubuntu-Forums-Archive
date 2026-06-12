---
title: "Quick question about virtual machine softwares...disk required?"
date: 2010-05-13
forum: General Help
---

### Post by aklo on 2010-05-13
Alright story is: i needed apache tom cat to work on my project, i don't wish to install it in ubuntu so i can keep my system clean and fast.

I installed virtual box OSE. Do i need a disk to run? Cause it says "Fatal no bootable medium found system halted"

Edit: alright i inserted my winxp disk and now it is installing, i need to know if any change i make will damage my computer?
Since i allocated only 10GB to this virtual disk, now it is formatting it in NTFS...i hope it won't have any conflict with ubuntu's ext4 file system...

---

### Post by quixote on 2010-05-15
(Hi aklo :D.  You're really on a vbox run, aren't you?)

Vbox virtual machines are completely limited to their assigned space.  They won't affect your host system in any way.

---

### Post by gadolinio on 2010-05-15
> **quixote said:**
> (Hi aklo :D.  You're really on a vbox run, aren't you?)

Vbox virtual machines are completely limited to their assigned space.  They won't affect your host system in any way.
+1.

What you do inside the virtual machine's window will modify only that computer, more specifically the virtual drive it's using (it's a .vdi file located in /home/your_user_name/.VirtualBox/HardDisks).

---

