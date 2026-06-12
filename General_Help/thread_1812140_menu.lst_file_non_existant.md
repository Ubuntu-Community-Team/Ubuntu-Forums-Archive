---
title: "menu.lst file non existant ?"
date: 2011-07-25
forum: General Help
---

### Post by Hirobian on 2011-07-25
***-/-/-/-SOLVED-/-/-/-***

I am following a guide on how to change the boot order using a terminal on Ubuntu.

Link: ( [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS) )

At the **Back Up Grub Settings** part I do the " /boot/grub/menu.lst_backup " command and input my password and it gives me this: 
name@name-laptop:~$ /boot/grub/menu.lst_backup
bash: /boot/grub/menu.lst_backup: No such file or directory

So I hesitatingly decide to skip this part.
At the **Open in a Text Editor **part I do the " /boot/grub/menu.lst " command in the terminal and it opens an empty file and I get a hunch...I go into /root/grub to check if the file even exists and I cannot even find the menu.Ist file anywhere.

I am guessing there may be a problem or the file is simply named differently for some reason, anyways I need help to figure out whats wrong or where the menu.Ist file is.

---

### Post by garvinrick4 on 2011-07-25
> **Hirobian said:**
> I am following a guide on how to change the boot order using a terminal on Ubuntu.

Link: ( [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS) )

At the **Back Up Grub Settings** part I do the " /boot/grub/menu.lst_backup " command and input my password and it gives me this: 
name@name-laptop:~$ /boot/grub/menu.lst_backup
bash: /boot/grub/menu.lst_backup: No such file or directory

So I hesitatingly decide to skip this part.
At the **Open in a Text Editor **part I do the " /boot/grub/menu.lst " command in the terminal and it opens an empty file and I get a hunch...I go into /root/grub to check if the file even exists and I cannot even find the menu.Ist file anywhere.

I am guessing there may be a problem or the file is simply named differently for some reason, anyways I need help to figure out whats wrong or where the menu.Ist file is.


That would be for grub-legacy (grub) which is from 9.04 ubuntu and back. Ubuntu now uses
grub2 (grub-pc)
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by seawolf167 on 2011-07-26
Edit the config file

```
gedit /etc/default/grub
```Change the line that says

```
GRUB_DEFAULT=0
```to

```
GRUB_DEFAULT=**X**
```where you replace the X with the menu   item number (starting with 0 for the first entry) of Windows you see in   grub upon boot.

Then run 

```
sudo update-grub
```

---

### Post by gnu-buntu on 2011-07-26
*This is the best way to change grub2 boot order*:

[INDENT][http://danielsmedegaardbuus.dk/2011-01-31/changing-grub2-boot-order-the-right-way/](http://danielsmedegaardbuus.dk/2011-01-31/changing-grub2-boot-order-the-right-way/) [/INDENT]

I just ran the procedure, and it works perfectly. It also makes sense. Follow the instructions exactly and be sure to run $ sudo update-grub .

(If you change /etc/default/grub, you'll have problems the next time the o/s upgrades.)

Quick summary, assuming you want a foreign o/s, e.g., Windows to be first in the list and run as default:
[INDENT]you@yourhost:~$ sudo mv /etc/grub.d/30_os-prober /etc/grub.d/07_os-prober
you@yourhost:~$ sudo update-grub[/INDENT]

---

### Post by Mark Phelps on 2011-07-27
> **gnu-buntu said:**
> ... (If you change /etc/default/grub, you'll have problems the next time the o/s upgrades.)


Actually, it might not ...

First, if you replace the default "number" of the stanza you want launched with the text line, it won't change in the future.

Second, GRUB v1.99RC uses nested menus, meaning that only the most current kernel shows by default, the others are pushed down into a submenu.  This means that the relative numbering of the other entries does not change when new kernel lines are added (as with updates).

---

### Post by gnu-buntu on 2011-07-28
> **Mark Phelps said:**
> Actually, it might not ...

First, if you replace the default "number" of the stanza you want launched with the text line, it won't change in the future.

Second, GRUB v1.99RC uses nested menus, meaning that only the most current kernel shows by default, the others are pushed down into a submenu.  This means that the relative numbering of the other entries does not change when new kernel lines are added (as with updates).

Thanks for clarifying that. Yes, I did notice a line in the GRUB menu that refers to prior linux verions. So maybe the method I cited isn't "the best" but rather, "another" way.

---

### Post by Hirobian on 2011-08-23
Sorry that I haven't replied in a while, I got cought up in an unexpected vacation and had left my laptop at home. I will now try the suggestions

---

### Post by Hirobian on 2012-03-31
Again sorry for the very very long wait before an update. I have been very busy with my studies and have only had the time to take peeks now and then.

I did more research about 2 months ago and found a program called "Startup manager" and that fixed my problem.

Thank you for the previous help, I am sure I would have been able to do the changes manually with code and your help if I had more experience at the time. I still do not know much programming as of this moment, however I am steadily learning. ^^

---

