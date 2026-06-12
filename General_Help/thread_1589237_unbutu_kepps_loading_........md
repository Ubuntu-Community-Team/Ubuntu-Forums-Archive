---
title: "unbutu kepps loading ......."
date: 2010-10-06
forum: General Help
---

### Post by roopakjada on 2010-10-06
hi every one :)
i recently downloaded unbutu and then burned the image to a cd im running windows
and installed ubuntu alsogisde it but i have a problem :( after rebooting the unbutu icon comes up and the dots keep moving (i dont know how else to describe it ,probably booting i guess ) and thats all that happens i waited but nothing ever happens could you please help me :P 
 
information i guess you need to know
current os :- windows seven X86 
no of partitions :- 5 (250 gb hard disk,STATA )
windows installed on :- c drive 
tried to install ubuntu :- d drive 
 
system configuration
core2 duo 
4 gb ram 
946GMX s2 motherboard 
nvidia graphic card (1 gb )
 
 
i tried many times i even waited for an hour but nothing just happens :confused:
 
PLEASE HELP ME :D

---

### Post by an0dos on 2010-10-06
When you're booting up the computer you should see a screen with text that lets you start either Windows 7 or Ubuntu. Highlight ubuntu and press "e" to edit the line. Add the word ```
nomodeset
``` before the words "quiet splash". Then hit the key sequence to continue booting (I forgot what it was but it should be on the bottom of the screen).

If this works, then you should do the following:

*press "Alt-F2"
*type ```
sudo gedit /etc/default/grub
```
*add the word "nomodeset" to the line that says GRUB_CMDLINE_LINUX="" in between the quotation marks so that it says ```
GRUB_CMDLINE_LINUX="nomodeset"
```
*Save the file
*Press "Alt-F2" and run the command ```
sudo update-grub
```

This procedure will make the change permanent.

---

### Post by roopakjada on 2010-10-06
thanks ill post back when ill see if it works

---

