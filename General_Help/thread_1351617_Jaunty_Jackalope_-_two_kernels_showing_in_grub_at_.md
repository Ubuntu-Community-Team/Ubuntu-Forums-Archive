---
title: "Jaunty Jackalope - two kernels showing in grub at start up, can I remove one?"
date: 2009-12-10
forum: General Help
---

### Post by ozguitarplayer on 2009-12-10
Hi,
I now have two kernels displayed in grub at start up. I have also noticed that the operating system (Jaunty Jackalope) has doubled. Is this consistent with having two kernels and if so how do I remove one of them?

---

### Post by bumanie on 2009-12-10
It is a good idea to have a 'spare' kernel that is known to work in case something goes wrong with your present one or an update wrecks it. I would advise not to remove the older one. Most users  have at least one kernel as a back-up. However if you want to remove it, go to synaptic, type 'linux-image' (without the quotes) in search and then find the kernel you wish to remove. Right click, choose "Mark for complete removal" and the kernel will be removed. Then do > sudo update-grub in terminal.

---

### Post by ozguitarplayer on 2009-12-10
Thanks bumanie, 
The only reason I thought to remove it is because (and this is an an assumption Ha!!) the CPU is working a lot harder than it uesd to and I thought that the extra kernal might be doing this?
Also...is it correct that the operating system will double in size if there are two kernels?

---

### Post by lmarmisa on 2009-12-10
Grub shows you two (or more) kernels options at start up, but only one kernel is selected and only one kernel is running in your computer.

The best selection is the newest kernel (99.99% sure). Other kernels are only backup solutions.

So, don't worry at all.

Best regards,

Luis

---

### Post by ozguitarplayer on 2009-12-10
thanks,
I'll leave it alone and keep one as a back up. I guess I was just curious as to why the size of the operating system went from 3.5 Gb to 7Gb

---

