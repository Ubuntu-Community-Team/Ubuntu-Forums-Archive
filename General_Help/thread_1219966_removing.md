---
title: "removing"
date: 2009-07-22
forum: General Help
---

### Post by happyhacker on 2009-07-22
I have installed ubuntu on a laptop and it dual boots. Trouble is is asks which OS to use and I have to tab down to select windows. How do I either:

1. get it to default to Windows startup (after timeout)?

2. Uninstall ubuntu leaving windows with the whole drive for use (is there some instructions for this)?

thanks.

---

### Post by prem1er on 2009-07-22
You can accomplish both options, which one would you like help with?

---

### Post by credobyte on 2009-07-22
First option ( setting Windows as your default choice ): [http://www.easy-ubuntu-linux.com/grub-menu-default.html](http://www.easy-ubuntu-linux.com/grub-menu-default.html)
Second option: boot from your LiveCD, remove Ubuntu partition and merge it with an existing Windows partition.

---

### Post by happyhacker on 2009-07-22
I tried:

[COLOR="Red"]1.Startup Ubuntu as usual 
2.Press Alt-F2 (i.e., depress 'Alt' and, without releasing it, press 'F2') for a 'Run Application' dialogue box 
Type 'gksudo gedit /boot/grub/menu.lst' (without the quotation marks) 
3.When prompted, enter your password. See "Ubuntu Root Access" if you have trouble at this point. You will then be presented with a GEdit window in which the configuration file for grub is reflected. 
3.Around the 14th line of the file, you will see the entry "default 0".[/COLOR] 

That file appears completely empty. In fact it looks like a new file.

---

### Post by Cheesemill on 2009-07-22
You must have a typo, your /boot/grub/menu.lst must exist or you couldn't boot either OS.

PS - It's menu.lst not menu.1st , copy and paste the following if you are unsure
```
gksudo gedit /boot/grub/menu.lst
```

---

