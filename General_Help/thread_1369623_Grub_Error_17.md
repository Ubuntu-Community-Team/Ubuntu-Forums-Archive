---
title: "Grub Error 17"
date: 2010-01-01
forum: General Help
---

### Post by Hnykda on 2010-01-01
Hi, i can`t solve my problem.
I have dualboot with WinVista and Ubuntu 9.04

I did a stupid thing, i tried to format my linux part of disk from windows-I got BSOD. 
Now, when I try to boot my system, I get something like:
Grub 1.5 is loading...

Error 17

----

And here it stuck and I must restart my PC. I tried to find on the google but im confused. 

I can boot my PC via ubuntu LiveCD and is possible to see Windows folders.
I dont wanna safe my Linux part, i want to delete, but i wanna safe my windows vista. It`s possible to change grub, or just skip it and start Vista? Any idea? Thanks



P.S When I`m trying to change grub throw terminal: find /boot/grub/stage1

i got: "Error 15: File not found"

---

### Post by louieb on 2010-01-01
Your not the 1st to think I'll just delete Ubuntu and the PC will automatically boot back to window. You have to put the Windows IPL code back in the MBR. lots of ways described here   [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

### Post by Hnykda on 2010-01-01
I tried this metod: [B]Replace GRUB in MBR with ms-sys
But i got error: "E:Couldnt find package ms-sys
[/B]

---

### Post by Leppie on 2010-01-01
install lilo:
```
$sudo apt-get install lilo
```

restore the mbr:
```
$lilo -M /dev/sda mbr
```

---

