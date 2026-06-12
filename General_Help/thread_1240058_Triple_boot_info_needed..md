---
title: "Triple boot info needed."
date: 2009-08-14
forum: General Help
---

### Post by Couto on 2009-08-14
Currently I am dualbooted with Windows 7 and Ubuntu 9.04.

I was thinking of installing Fedora also, I've never used Fedora before so I don't know the options in the partition manager during its install.

Will I be able to share the same drive with all 3 of these OS and get the Menu @ Boot to select my OS?


Also is there anyway to edit my grub menu? I have 2 of the same kernal'd ubuntu on there and I'd like to clean it up a bit, lol.

Thnaks for the help, once again.

---

### Post by Couto on 2009-08-14
Bump. :KS

---

### Post by soapBAR2 on 2009-08-14
```
sudo nano /boot/grub/menu.lst
```

Or your environment should have a built-in GRUB editor, check the settings menu.

---

### Post by sonu 1807 on 2009-08-14
For editing grub

1. Open terminal and enter sudo gedit /boot/grub/menu.lst
2. Edit it (delete one of the double entries) and then save and close

Fedora after installation won't recognise Ubuntu. Windows, however, will be recognized.

Do you know how to reinstall ubuntu grub?

---

### Post by Couto on 2009-08-14
> **sonu 1807 said:**
> For editing grub

1. Open terminal and enter sudo gedit /boot/grub/menu.lst
2. Edit it (delete one of the double entries) and then save and close

Fedora after installation won't recognise Ubuntu. Windows, however, will be recognized.

Do you know how to reinstall ubuntu grub?

Well, can I install Ubuntu grub outside of Ubuntu, since Fedora wont recognize Ubuntu?

---

### Post by sonu 1807 on 2009-08-14
Sorry, for late reply you can reinstall ubuntu grub. Or you can add ubuntu to fedora bootloader

First Option-: Insert Ubuntu live CD

When you get to the desktop open a terminal and enter. 

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.

Now you will have to add fedora to ubuntu grub

Again in Ubuntu open a terminal and type 

sudo gedit /boot/grub/menu.lst

Suppose /boot of fedora is installed on the first harddisk in x partition, then

You have to add these lines

title Fedora 11
root (hd0,x-1)
configfile /boot/grub/menu.lst (if /boot is not a separate partition)

OR         /grub/menu.lst (if /boot is a separate partition)

Personal Opinion: Ubuntu is better then Fedora; You don't need it

---

### Post by Couto on 2009-08-14
> **sonu 1807 said:**
> Sorry, for late reply you can reinstall ubuntu grub. Or you can add ubuntu to fedora bootloader

First Option-: Insert Ubuntu live CD

When you get to the desktop open a terminal and enter. 

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.

Now you will have to add fedora to ubuntu grub

Again in Ubuntu open a terminal and type 

sudo gedit /boot/grub/menu.lst

Suppose /boot of fedora is installed on the first harddisk in x partition, then

You have to add these lines

title Fedora 11
root (hd0,x-1)
configfile /boot/grub/menu.lst (if /boot is not a separate partition)

OR         /grub/menu.lst (if /boot is a separate partition)

Personal Opinion: Ubuntu is better then Fedora; You don't need it

Thank you but a couple things:

I just want to try Fedora.
I don't have Ubuntu on CD nor USB (I cleared it for Fedora)
Do you know anything about syslinux? [http://ubuntuforums.org/showthread.php?t=1240127](http://ubuntuforums.org/showthread.php?t=1240127)

---

### Post by sonu 1807 on 2009-08-14
No, I have got no idea about syslinux (heard the name for the first time; If you really install fedora then don't forget to add RPMFusion repository). I am not sure , but i think any live linux CD or usb will do the job  of reinstalling ubuntu grub or I think even in fedora you have to first mount ubuntu and then type sudo -s in terminal and then follow the steps to reinstall the grub of ubuntu (not sure though)

---

### Post by Couto on 2009-08-14
> **sonu 1807 said:**
> No, I have got no idea about syslinux (heard the name for the first time; If you really install fedora then don't forget to add RPMFusion repository). I am not sure , but i think any live linux CD or usb will do the job  of reinstalling ubuntu grub or I think even in fedora you have to first mount ubuntu and then type sudo -s in terminal and then follow the steps to reinstall the grub of ubuntu (not sure though)

Okay thank you for all your help, I just thought of going on my Windows partition and doing the syslinux stuff there, I sat here for hours looking for help, and my help was 1minute away.

---

