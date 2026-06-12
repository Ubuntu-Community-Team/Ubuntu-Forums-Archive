---
title: "Windows 7 dual boot"
date: 2009-11-14
forum: General Help
---

### Post by Fruguy101 on 2009-11-14
I bought a Toshiba laptop a few weeks ago that has Windows 7 on it. I'm not new to linux or ubuntu, but i'm not an expert.
 
I have installed ubuntu 9.10 onto another system that has xp on it. when i was trying to get xp to be the default os loaded, i could not locate the file menu.lst in the grub folder. I looked around and finally figured out to login as the root user and edit the grub config file to load xp by default. i was never able to find the menu.lst file. i tried entering sudo gedit /boot/grub/menu.lst but all it opened was a blank text doc. 
 
Does anybody know why i couldn't find that particular file to edit for the grub bootloader? Also, if i dual boot my win7 laptop, do you think i would have to do the same thing on it as i did with my xp desktop?

---

### Post by wilee-nilee on 2009-11-14
Startup manager in Ubuntu will let you change the boot order and time out, even with grub2

---

### Post by RedSingularity on 2009-11-14
Try restoring grub.  Follow [these](http://ubuntuforums.org/showthread.php?t=224351) steps.

---

### Post by wilee-nilee on 2009-11-15
> **RedSingularity said:**
> Try restoring grub.  Follow [these](http://ubuntuforums.org/showthread.php?t=224351) steps.

That is a link for changing legacy grub not grub2, which is what the OP will have if they install 9.10.

---

### Post by garvinrick4 on 2009-11-15
Try alt/f2   type in "gksudo nautilus" without qoutes. Then run.

Should open nautilus and say root instead of login name.

If it doe's you should be able to open boot icon to
to menulst and then open with gedit and should have root
privileges to edit.  

Ubuntu defaults to not give out certain root privileges and 
config files are some of them. Long story takes investigating. 

I think this could be the simplest way. Try it.  Anyway around
it nautilus must open with root and not your login name.

---

### Post by diaco on 2009-11-15
Ubuntu 9.10 uses grub2 and editing menu.lst is no longer the case. I think using startup manager is the best way

---

### Post by Fruguy101 on 2009-11-15
Where is startup manager located? i can't seem to find it in either preferences of administration

---

### Post by wilee-nilee on 2009-11-15
You have to install it from synaptic.

---

### Post by diaco on 2009-11-15
Ubuntu 9.10 uses grub2 and editing menu.lst is no longer the case. I think using startup manager is the best way

---

### Post by Fruguy101 on 2009-11-15
> **wilee-nilee said:**
> You have to install it from synaptic.
 
 
Thanks for the info. I've looked several places but didn't find that. I'm still learning quite a lot about linux.

---

### Post by Lucky75 on 2009-11-15
if you want to edit your grub2 menu, it's in /boot/grub.cfg

---

### Post by wilee-nilee on 2009-11-15
> **Fruguy101 said:**
> Thanks for the info. I've looked several places but didn't find that. I'm still learning quite a lot about linux.

Did you find it in synaptic? Since every time I install I automatically open the extra repositories in software sources, so if it is not there yet, go to software sources and tick all the extra stuff. I don't know if this is what is needed to get it loaded but it is always in synaptic.

So you understand that it is not installed in the stock distro but should be in synaptic for installation, you just have to scroll down and find it, after using the quick search or other search in synaptic.

---

### Post by Fruguy101 on 2009-11-15
yeah, i found it and got it installed. @lucky75--i found out about the grub.cfg the other day, but thanks for the tip anyways.

---

