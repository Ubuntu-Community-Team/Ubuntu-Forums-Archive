---
title: "grub: next time boot"
date: 2010-10-16
forum: General Help
---

### Post by poxet on 2010-10-16
hello there :popcorn:
i was just wondering if there ever were something like a 'next time boot' command, something like a 'next time boot windows', but i don't want to set it as default, i want just to boot it once without having to choose it from the list, so one could just enter that command, click reboot and go away and then come back and have windows booted... is there something like that?

greetings

---

### Post by drs305 on 2010-10-16
Take a look at the "grub-reboot" command. I've not used it since Grub 2 first came out - it's designed for what you want.

Take a look at the man page:
```
man grub-reboot

```
And please post your experiences with it.

---

### Post by poxet on 2010-10-19
> **drs305 said:**
> Take a look at the "grub-reboot" command. I've not used it since Grub 2 first came out - it's designed for what you want.

Take a look at the man page:
```
man grub-reboot

```And please post your experiences with it.

well you my friend are quite the wise man.
that was exactly what I needed to read.
i greet you and i salute you =D>
live long and prosper

two other things:
1) for the other newpies as myself who fall into this thread:
the command to run is:
```
sudo grub-reboot X
```
where X is the number of the item in the grub's boot list you want to choose (starting from zero, that is, if windows is 5th on your list, to choose it you should enter 4)
important: before you run this thing you must edit the file:
```
/etc/default/grub
```
and set
```
GRUB_DEFAULT=saved
```
and then run:
```
sudo update-grub
```
and THEN you are good to go

2) another question for [[COLOR=#D40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945") or any of the gentle wise men of this forum:
now I want to create some sort of button that one would click and would run the grub-reboot thing and prompt some sort of alert that would go 'grub reboot ok, wanna reboot now, buddy?' and one could go OK or CANCEL... i don't know how to this... i don't expect the full code either! but i want to know how to achieve this... if using a shell script or a program in c or whatever...

greetings, fellow ubuntuers

---

### Post by drs305 on 2010-10-19
I'm not great at scripting, but here is a basic script. It would open a terminal, display the current "nextboot" setting from /etc/grub/grubenv, display the current menu entries from /boot/grub/grub.cfg, have you pick a number, and then set it for the next boot. Finally it will show the new "next boot" setting. You press any key to close the terminal at the end.

You may have to tweak the "cut" sections to get the menuentry displays to your liking.

Save the file and make it executable.

To make a launcher, right click the panel, add to panel, run in terminal, with the command: ./<path>/nextboot.sh

If you wanted to avoid having to type your password, you could put an entry for "grub-reboot" in the /etc/sudoers file. There are posts describing how to do that.

> 
#!/bin/bash
clear
grep "saved_entry" /boot/grub/grubenv
grep "menuentry" /boot/grub/grub.cfg | cut -d "'" -f 2 | nl
echo " "
echo "Which number would you like to run on the next boot?"
read NEXTBOOT 
sudo grub-reboot $NEXTBOOT
grep "saved_entry" /boot/grub/grubenv
read p
exit

---

