---
title: "How do you make the noapic option is selected  when ubuntu starts after an install"
date: 2010-10-13
forum: General Help
---

### Post by MaxTesla on 2010-10-13
To make Ubuntu work on my computer I need to select the noapic option
 

 NOW
 

 How do I make certain that the noapic option is selected always when ubuntu starts after ubuntu has been installed?


I would like to install Ubuntu 10.10 on my computer togheter with windows 7

---

### Post by MaxTesla on 2010-10-13
How do i get my installed version of ubuntu 10.10 64 bit version to start with the noapic option

---

### Post by MaxTesla on 2010-10-13
I found it

When the computer starts you use the arrow keys to select ubuntu then you press E and use the arrow keys again to go behind the words quiet splash and press space bar and then type in noapic and then press ctrlx

---

### Post by plucky on 2010-10-13
> **MaxTesla said:**
> I found it

When the computer starts you use the arrow keys to select ubuntu then you press E and use the arrow keys again to go behind the words quiet splash and press space bar and then type in noapic and then press ctrlx

Why not edit /etc/default/grub and put the option in there.When you then update-grub,it will always be there.

Read [Grub2 Basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2)

Please do not bump your thread after 1 hour.

Good Luck

---

### Post by MaxTesla on 2010-10-13
The problem was that I couldnt get Ubuntu to start at all, so first I needed to get it to start
 
When inside ubuntu I was later able to via the terminal update the grub so that it always start with the noapic

---

