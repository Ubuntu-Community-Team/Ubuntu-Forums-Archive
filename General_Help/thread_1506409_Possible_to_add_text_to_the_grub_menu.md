---
title: "Possible to add text to the grub menu?"
date: 2010-06-10
forum: General Help
---

### Post by listerdl on 2010-06-10
Hi is it possible to add text to the grub menu?

I was thinking of adding a Lost Please Return To etc etc text...

That possible?

thanks!

---

### Post by ba_saish on 2010-06-11
not really sure what you want to do, but in the /boot/grub/menu.lst file you can give any text in the title field. What should happen when some one selects that text is dependent of the lines below it. So if you know what to commands to give, I guess you can add any text in the title field.

---

### Post by Mark Phelps on 2010-06-11
> **listerdl said:**
> Hi is it possible to add text to the grub menu?

I was thinking of adding a Lost Please Return To etc etc text...

That possible?

thanks!

Realize that with the latest GRUB2 installed with 10.04, if you only have one OS on your machine, you will no longer SEE a GRUB menu.  The new default is to boot directly into the default selection without even showing a menu.

---

### Post by drs305 on 2010-06-11
The easiest way to add text to the G2 menu is probably to create a "dummy" entry in a custom file.

As root, open the /etc/grub.d/40_custom file:
```
gksu gedit /etc/grub.d/40_custom
```

You can make the title anything you want, and I've found it's simplest just to add a common Grub2 command to the entry to make it a legitimate Grub2 entry. Here is an example:

> 
menuentry "**[COLOR="DarkRed"]Add your text here[/COLOR]**" {
	insmod ext2
}


Now, if you want the text at the bottom of the screen all you have to so is save the file and update-grub. This is because the scripts in the /etc/grub.d folder are run in accordance with their name, and the 40_custom script will run last.

If you want the text at the top, save the file as "06_custom" and it will be placed before any other menu entries. You will also need to make /etc/grub.d/06_custom executable with the following command:
```
sudo chmod +x /etc/grub.d/06_custom
```

You can add more than one entry, or add one at the top (06_custom) and another at the bottom (40_custom). Getting them elsewhere would take a lot more effort.

When finished, don't forget to incorporate the changes into grub.cfg:
```
sudo update-grub
```

---

