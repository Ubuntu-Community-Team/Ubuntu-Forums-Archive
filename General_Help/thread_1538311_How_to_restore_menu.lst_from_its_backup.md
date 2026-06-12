---
title: "How to restore menu.lst from its backup"
date: 2010-07-24
forum: General Help
---

### Post by Vendettaseve on 2010-07-24
Hey

Im running ubuntu 10.04 and I recently had a little adventure whilst trying to disable KMS and deleted all the stuff out of the # kopt line and added the nomodeset thing.

This was obviously a bad idea


Now I crash to easybox everytime I try to boot, how do I restore the backup of said file that I noticed beside it in the folder. Also I saved one to my desktop.

Thanks

V

---

### Post by WorMzy on 2010-07-24
Boot form a liveCD, mount your Ubuntu partition, and run 'gksu nautilus'. You should be able to copy the files over easily from there.

Or, press and hold Esc immediately after your computer turns on and POSTs, you should be shown your boot menu by doing that, and from there, you should be able to make temporary modifications to your boot options.

---

### Post by howefield on 2010-07-24
> **Vendettaseve said:**
> trying to disable KMS and deleted all the stuff out of the # kopt line and added the nomodeset thing.

This was obviously a bad idea

The above should sort you out, but just a quick point to say the instructions you were following didn't ask you to delete everything from the relevant line, only to add nomodeset to the end of it.

---

### Post by Vendettaseve on 2010-07-24
> **WorMzy said:**
> 
Or, press and hold Esc immediately after your computer turns on and POSTs, you should be shown your boot menu by doing that, and from there, you should be able to make temporary modifications to your boot options.

Im downloading the live CD now, but il try the second option first. Think you could toss some more detailed instructions in there, im a wicked noob sometimes.

Step by step if possible.

---

### Post by WorMzy on 2010-07-24
It's pretty self explanatory once you get into the boot menu. You just select the menu item you want to edit, and press 'e'. Then select the line you want to edit, and press 'e' again. Edit the line that you think you've messed up, and make it say what it should say. e.g. the kernel line should say something like
```
kernel /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 ro quiet splash
```

If you deleted the whole line before this happened, then reconstructing it may be difficult. So keep an eye out for other boot options in the boot menu, and use one of them instead of trying to fix the broken one.

---

### Post by Vendettaseve on 2010-07-25
Ah true, Il have to redo it via the liveCD with the old copypaste

thanks for your replys

---

### Post by Vendettaseve on 2010-07-25
I copy/pasted the missing line back in but am still getting the same error when I try to boot normaly. any idea?

---

### Post by Vendettaseve on 2010-07-25
> **Vendettaseve said:**
> I copy/pasted the missing line back in but am still getting the same error when I try to boot normaly. any idea?

Deleted the entire file and replaced it with the backup, works perfetly now. 


Many thanks all who replied

---

