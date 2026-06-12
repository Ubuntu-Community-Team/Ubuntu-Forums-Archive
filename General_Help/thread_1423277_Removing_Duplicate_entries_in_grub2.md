---
title: "Removing Duplicate entries in grub2"
date: 2010-03-06
forum: General Help
---

### Post by anderskitson on 2010-03-06
I have made a custom grub2 menu however, both the default and the custom show together. So my grub looks like the list below, the bolded entries are my custom ones. How do I get rid of the duplicates? I have tried apt-get remove and deleting old kernels. I am a bit lost. Thanks! in Advance.

ubuntu,linux ...
ubuntu,linux recovery
memtest
memtest
windows7
[B]windows7
ubuntu linux
ubuntu linux recover[/B]

---

### Post by spiky001 on 2010-03-06
hi dose each 1 of the linux kernels have different no after them?

---

### Post by anderskitson on 2010-03-06
They have the same # because I copied and pasted the grub.cfg menuentry code into the custom one and just renamed the titles so it would be perfectly clear for the user who doesn't want to know what version # it is.

---

### Post by spiky001 on 2010-03-06
it,s best to keep at least 1 old kernel just incase of problems with the new 1 so yo can still boot into os

---

### Post by anderskitson on 2010-03-06
Ok, Well how would I at least put the custom grub stuff at the top.

---

### Post by anderskitson on 2010-03-06
Ahah! I figured out what I needed to do I forgot to run "sudo update-grub2" after apt-get remove. Now it works. I will add the old kernels underneath for good measure Thanks.

---

### Post by mohansathish on 2010-03-06
well i understood that you wanted to have as 
ubuntu
Windows
*blah*
*blah*

To do so, you can edit grub.cfg. 
This can be done by enabling write mode for that. In terminal, type
    sudo chmod +w /boot/grub/grub.cfg
Then edit it by using 
    sudo gedit /boot/grub/grub.cfg

If i posted wrongly, please remove it   :D

---

### Post by anderskitson on 2010-03-06
> **mohansathish said:**
> well i understood that you wanted to have as 
ubuntu
Windows
*blah*
*blah*

To do so, you can edit grub.cfg. 
This can be done by enabling write mode for that. In terminal, type
    sudo chmod +w /boot/grub/grub.cfg
Then edit it by using 
    sudo gedit /boot/grub/grub.cfg

If i posted wrongly, please remove it   :D

I would have done that, but I am pretty sure grub2 doens't want you to. I figured out what I had to do but thanks anyways.

---

