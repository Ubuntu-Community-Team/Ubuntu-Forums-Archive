---
title: "please help"
date: 2009-11-22
forum: General Help
---

### Post by newby25 on 2009-11-22
[FONT=monospace]i wrote [/FONT]:
sudo gedit /boot/grub/menu.lst

a list came out
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3 
i change default   from 0  to 1 and then save.
after that i can not log on
when i choose ubuntu it asks me 

resume normal boot?
i press ok
and then i lets me to terminal or something.

can u tell me what to do?
cheers

---

### Post by lisati on 2009-11-22
Which version of Ubuntu are you using? Editing menu.lst won't work so well for 9.10

---

### Post by newby25 on 2009-11-22
im using 9.10

---

### Post by fluffman86 on 2009-11-22
You changed the default boot option from 0 to 1, or rather, from Ubuntu to Ubuntu's recovery console.

You can change grub back to the way it was by entering a root shell, and typing:
```
nano /boot/grub/menu.lst
```
where you can change the default boot entry back from 1 to 0.  Close the file by pressing CTRL+X (that's what ^X stands for), and save it with "Y".

Reboot with:
```
reboot now
```
And you should be able to get back into the GUI.

---

### Post by fluffman86 on 2009-11-22
Nvm.

---

### Post by Uncle Spellbinder on 2009-11-22
> **lisati said:**
> Which version of Ubuntu are you using? Editing menu.lst won't work so well for 9.10

It's not that it "won't work so well" in Ubuntu Karmic. It won't work AT ALL. There is no boot/grub/menu.lst in Karmic. Karmic uses Grub 2 now. Do a forum search. There are many threads on Grub 2.

---

### Post by fluffman86 on 2009-11-22
> **Uncle Spellbinder said:**
> It's not that it "won't work so well" in Ubuntu Karmic. It won't work AT ALL. There is no boot/grub/menu.lst in Karmic. Karmic uses Grub 2 now. Do a forum search. There are many threads on Grub 2.

I just posted basically the same thing.  That's true, unless he did an upgrade.  Grub doesn't upgrade to Grub2 just because you upgrade to Karmic.  :\

---

### Post by newby25 on 2009-11-22
THANX MATE
u really saved me
i won't mess it again
cheers

---

