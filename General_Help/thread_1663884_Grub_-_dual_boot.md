---
title: "Grub - dual boot"
date: 2011-01-10
forum: General Help
---

### Post by Meninspex on 2011-01-10
[SIZE=3][FONT=Arial]Previously dual booting between Ubuntu and XP I changed the delay time to 10 secs.  I recently upgraded Windows to Win7 Ultimate and the Grub booter reset the delay time to 30 secs.  I called up the menu.lst file in the terminal but find I can't edit it, nor is there a save option in the edit menu.  What am I doing wrong?

Ubuntu 10.04

Please be gentle with me as despite a long acquaintance with Ubuntu I still know b******* all about it.
[/FONT][/SIZE]

---

### Post by Zimmer on 2011-01-10
If it is a standard 10.04 install you are using the latest GRUB which does not edit in quite the same way as the legacy GRUB.

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

and have a look on the community help for pages on it, too.

You may need to edit one of the files in etc/grub.d
or etc/default/grub, depending on the changes required.

Also, you will need to have ROOT access to edit these files, too.

Editing menu.lst in the new GRUB is NOT a good idea, apparently. :)

---

### Post by Hippytaff on 2011-01-10
Welcome!
 
I didn't think there was a menu.lst file in grub2, which is what 10.04 uses.
 
Anyway you need to edit the /etc/defaul/grub file. You will see a timeout bit. Change that to whatever you want it to be. You might need to type
```

sudo update-grub

```
for the change to take effect.
 
[see here]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

---

