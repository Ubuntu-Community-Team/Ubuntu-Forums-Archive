---
title: "boot-up problem"
date: 2009-12-05
forum: General Help
---

### Post by hockey9876 on 2009-12-05
A recent update to my system disrupted its normal operation.
After boot up, it began looping between the dell start-up
screen and the grub info screen.  

In hitting escape to bring me to the boot screen, there are
no options listed.  I understand these come from the menu.lst
file.  Anyway, I can select c (command line) and proceed to 
boot in using single user mode (SUM).

Now, the curious thing is at the grub> prompt, I can do a 
cat /boot/grub/menu.lst and I get a file not found error.  However,
if I do a cat /boot/grub/menu.lst~, it displays the contents.
After booting up in SUM, I can cd /boot/grub and do an ls and
sure enough, menu.lst exists!  

The question is how can I get it to display the contents at a 
screen?  For one of my computers, I have MS Vista and Ubuntu loaded, on my other computer, linux is the only OS.  I'm no SA,
but do have some linux/unix experience.  What I don't know is how
to fix my current problem...

John

---

