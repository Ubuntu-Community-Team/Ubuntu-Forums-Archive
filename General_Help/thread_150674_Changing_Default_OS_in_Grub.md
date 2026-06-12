---
title: "Changing Default OS in Grub"
date: 2006-03-26
forum: General Help
---

### Post by Musicalmidget on 2006-03-26
Hello!

I'm a new user to Ubuntu and fairly new to Linux in general.  I've tinkered before but only now am I going "seriously" into it.  I've recently installed Ubuntu and I must say I'm very impressed.  I am however having a small problem and could use some help. :)

I'm currently dual booting Ubuntu with Windows XP (Home Edition) using Grub.  By default however, Grub selects Ubuntu Linux as the default operating system.  For the moment, I need to default to remain as Windows XP.  I've been looking into changing this, and I've gathered that in order to change the default, I need to modify the default line of /boot/grub/menu.lst.  Unfortunately though, that file is read only, and I've been unable to do so.

So firstly, is this in fact the correct way to change the default operating system in Grub?  Secondly, if so, how to I correctly modify the menu.lst file?  For the record, I've tried right clicking the file and navigating to properties in order to change the file permissions, however all of the check boxes on the permissions page are greyed out and I am unable to modify them.

Any advice would be appreciated.

Thank you. :)

---

### Post by sprinkles on 2006-03-26
Try opening a terminal and navigating to /boot/grub/, then type
sudo gedit menu.lst

Enter your password and you should be able to edit it.

---

### Post by 10101001011 on 2006-03-26
[QUOTE=Musicalmidget]

So firstly, is this in fact the correct way to change the default operating system in Grub?  Secondly, if so, how to I correctly modify the menu.lst file?  For the record, I've tried right clicking the file and navigating to properties in order to change the file permissions, however all of the check boxes on the permissions page are greyed out and I am unable to modify them.

Any advice would be appreciated.

Thank you. :)[/QUOTE]

Type the following:

```

user@LCARS:~$ cd /boot/grub
user@LCARS:/boot/grub$ sudo gedit menu.lst

```

Then just drag and drop your windows record above the Ubuntu one.

HTH

---

### Post by gazj on 2006-03-26
The only user who can change permissions of this file, or any file which is not in the home directories, is a user called root, (like windows administrator), although its not a wise thing to do, so if you want to edit this file the best thing to is to open it as the root user.

The good difference here is that you dont have to log out and log in as root everytime you need to make a system change,  All you have to do to open  the file as root is open a terminal, under Applications > Accessories > Terminal

then in the terminal type

```
sudo gedit /boot/grub/menu.lst
```

you will be asked for the root password, if you have just installed ubuntu you won't have one, but if you put your own password in, it will let you by.

just so you know the "sudo" part is the command that lets you do something as root, you can put it infront of any other command

if you want to open the graphical browser as root type in the terminal

```
gksudo nautilus
```

this means open a the nautilus browser as root in graphical mode

then just find your menu.lst and now you will be able to open it
either way is fine

as for booting windows, if i remember rightly, you need to change default 0 to default 1

if windows is the second operating system in the list


Hope you get it to work, Good luck, let me know how you get on.

---

### Post by Musicalmidget on 2006-03-26
Thanks everyone.  I've successfully changed the default OS and everything is working fine. :)

Thanks again.

---

### Post by till on 2006-05-03
Hello,

I tried exactly the steps you have suggested. After typing the command line 'sudo gedit /boot/grub/menu.lst' into Terminal I am prompted for my password. After entereing the password, nothing happens, the text editor does not open. The same happens when trying to open Nautilus as root via the Terminal: nothing opens. 
What could be the problem?

Kindest regards,
Till

[QUOTE=gazj]The only user who can change permissions of this file, or any file which is not in the home directories, is a user called root, (like windows administrator), although its not a wise thing to do, so if you want to edit this file the best thing to is to open it as the root user.

The good difference here is that you dont have to log out and log in as root everytime you need to make a system change,  All you have to do to open  the file as root is open a terminal, under Applications > Accessories > Terminal

then in the terminal type

```
sudo gedit /boot/grub/menu.lst
```

you will be asked for the root password, if you have just installed ubuntu you won't have one, but if you put your own password in, it will let you by.

just so you know the "sudo" part is the command that lets you do something as root, you can put it infront of any other command

if you want to open the graphical browser as root type in the terminal

```
gksudo nautilus
```

this means open a the nautilus browser as root in graphical mode

then just find your menu.lst and now you will be able to open it
either way is fine

as for booting windows, if i remember rightly, you need to change default 0 to default 1

if windows is the second operating system in the list


Hope you get it to work, Good luck, let me know how you get on.[/QUOTE]

---

