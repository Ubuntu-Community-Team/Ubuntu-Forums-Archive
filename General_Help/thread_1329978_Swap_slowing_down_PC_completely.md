---
title: "Swap slowing down PC completely"
date: 2009-11-17
forum: General Help
---

### Post by Padakwaak on 2009-11-17
Hi,

I would like to know if there's a way of reducing the priority at which the memory -> swap partition and and swap partition -> memory process is running. Its not like its using too much CPU cycles, like when running the harddrive in PIO mode - it simply slows down all my applications to such an extent that they don't respond at all (fading to gray)!

I'm on Karmic x64 with a Dell 9400 (3.2GB of RAM & 100GB SATA), using Gnome. My swap partition size is 3GB - although I've never seen it using more than 1GB. 
I'm often running 1 or more VirtualBox instances of Windows 7 or XP which takes like 1GB of RAM each. When I leave one of them inactive for a while, Ubuntu will automatically start to move its allocated memory to the swap partition, slowing my PC to such an extent that I can't even resume/end-task the inactive virtualmachine.

I would appreciate it if someone could give me suggestions to this problem of mine.

Thank you in advance.

---

### Post by Ahadiel on 2009-11-17
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Look up swappiness.

---

### Post by Padakwaak on 2009-11-17
Thanks. I've now set swappiness to 0. I hope that its the solution I'm looking for...

---

