---
title: "After GRUB, screen goes blank"
date: 2011-02-05
forum: General Help
---

### Post by sarumantlor on 2011-02-05
Hello everyone, I just installed ubuntu 10.10 did a clean install, formating the previous ones. 
Install completed succesfully, rebooted, entered in GRUB, chose linux, linux starts the my screen goes black, there is no signal coming to my monitor, linux runs fine though i think because i hear the ubuntu login drum :D
I press ctrl+alt+F1, but can't get to console either, the screen is looking for input signal...

Should note the I have a Palit NVdia 9600GT gpu because i saw that people with NVdia card sometimes have similar problems...

Any ideas?

---

### Post by wojox on 2011-02-05
When you get to Grub press "E" for edit

Add "nomodeset" to the end of the kernel line.

Press "B" to boot.

---

### Post by sarumantlor on 2011-02-05
Thnx! It worked

---

