---
title: "memtest update"
date: 2011-12-19
forum: General Help
---

### Post by Mr Nemo on 2011-12-19
Does anyone know how I can update memtest to the newest version (4.20). I found the program on memtest.org, but i don't know how to install it in ubuntu.

---

### Post by seawolf167 on 2011-12-19
Any particular reason you want to update memtest86+? Is the current one not working? Can you simply use a LiveCD?

---

### Post by azmyth on 2011-12-19
memtest is in the repo. latest version is 4.20 at least for 11.10. 

sudo apt-get update memtest86+
or
sudo apt-get install memtest86+

It'll give you a memtest choice in grub that you can use on boot.

---

### Post by Mr Nemo on 2011-12-20
Thanks ill try that.

> seawolf167              **Re: memtest update**
         Any particular reason you want to update memtest86+? Is the current one not working? Can you simply use a LiveCD?     I have a dell xps 15 with the new(ish) sandy bridge processor. My memtest wasn't working and when I googled it, apparently any memtest before 4.20 won't run due to an incompatability with the processor. So i figured id give it a shot and see if i could update it.

---

