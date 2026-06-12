---
title: "Can't Get Grub Recovery Mode Menu To Boot Up"
date: 2011-04-30
forum: General Help
---

### Post by bry72 on 2011-04-30
Hey Guys,

I need some help regarding the recovery mode in the Grub menu.

I  started a thread over in installations and upgrades in which I was  trying to upgrade from Ubuntu 10.04 to 10.10 using the upgrade manager. My computer froze in  the middle of the process, requiring me to restart my computer.  When I  try rebooting Ubuntu, I get an error message "The configuration defaults for Gnome power manager have not been installed correctly" and then a blank screen.  No mouse pointer, no cursor.  It will not take me to the Ubuntu desktop screen.

I've already found the sudo commands I can run to try and fix Ubuntu.  They are as follows:

sudo apt-get clean  (If the problem is not having enough free hard drive space)
sudo dpkg --configure -a  (If the problem deals with the upgrade installation process) 

However, what I can't get is the terminal to come up to run these commands.

In  the other thread I started, someone mentioned that in the Grub menu,  you can choose "recovery mode", hit "enter" to boot it, and it will give  you a menu of options to choose from.  However, when I choose "recovery  mode" and hit "enter", I do not get a menu but instead 3 pages of data  about my computer that ends with this:

"Begin:  Running/scripts/init-bottom...
  Done. "

It gives me a blinking cursor at the very end but I cannot type anything and I cannot page up to see the 3 pages of data.

What I am looking for is a way to get to the recovery mode menu OR somehow open up a terminal so I can run the sudo commands.

My computer automatically logs me in, so I do not get a login screen and Ctrl+Alt+F1 does not work for me.

Anyone know how I can open a terminal with only access to the Grub menu?  Perhaps a BASH command that I can use in the command line that will open up a terminal?

To  summarize:  My computer does not boot Ubuntu.  I get an error message  followed by a blank screen.  It does not go into the desktop screen so I  cannot choose Applications->Accessories->Terminal.

My Grub  menu consists of Ubuntu and it's version, Ubuntu and it's version with  recovery mode, memtest, and Windows XP (I have a dual boot system).  In  the Grub menu, I can select "e" for edit, "c" for command line and  "enter" to boot either regular Ubuntu OS or Ubuntu recovery mode.   "Sudo" commands are not recognize if I choose the command line for  either Ubuntu OS or recovery mode.

I have a Live CD for 10.04 but you cannot run sudo commands because you do not have access to root on the Live CD.

Hopefully that is enough detailed information.  If you need more info, let me know.

---

### Post by bry72 on 2011-05-01
Anyone have any suggestions?

---

### Post by snlzkn on 2011-09-21
Same happened to me as well. Are there any grub parameters we can change that can give us some kind of shell access to fix the broken packages?

---

