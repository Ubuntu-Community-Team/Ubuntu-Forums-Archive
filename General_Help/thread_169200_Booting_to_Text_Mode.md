---
title: "Booting to Text Mode"
date: 2006-05-02
forum: General Help
---

### Post by topquarck on 2006-05-02
hi all;

sometimes I want to boot my distro to the text mode Only (no need to boot to the graphical interface to save memory and power)....
Some poeople told me to write this option on boot : init 3
but the problem is I don't know where to write this command. when the computers boots and grub loads, I have 2 options: either to press "e" or "c". but the command doesn't work in either of them....](*,) 

SO, I need to know how to boot in text mode (only for one time NOT parmenently) .
If any one can help me please .......!!!:confused: 

thanx alot

---

### Post by dlai on 2006-05-02
When entering grub you can choose between rescue mode and the normal boot...So you choose rescue mode kernel(at least that is what i think it is named, usually it is number two from the top)...
To go into grub, press a key when the countdown begins in the beginning of your boot...

---

### Post by Sef on 2006-05-02
> SO, I need to know how to boot in text mode (only for one time NOT parmenently) .

When you boot into text mode, you will be offered the choice of making it your default or not.

---

### Post by dcstar on 2006-05-02
> **topquarck]hi all said:**
> (*,) 

SO, I need to know how to boot in text mode (only for one time NOT parmenently) .
If any one can help me please .......!!!:confused: 

thanx alot
Open a terminal:
```
sudo rm /etc/rc3.d/S13gdm
```
When booting in Grub: press "e", add "3" **to the end** of the long line on the screen, then press "b" to boot to Run Level 3 (which now will not run X).

---

### Post by topquarck on 2006-05-02
sorry, but non of the ways worked ....
Any othr solution????

---

