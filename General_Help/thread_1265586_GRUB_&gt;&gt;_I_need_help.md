---
title: "GRUB &gt;&gt; I need help"
date: 2009-09-13
forum: General Help
---

### Post by mustafa2osman on 2009-09-13
[B][COLOR=Sienna][I]HOLLA


[/I][/COLOR][/B][COLOR=Sienna][COLOR=Black][SIZE=3]I messed up with my GRUB configs (( installing grub2 , remove grub 0.97 , remove grub2 , and re-install old grub )) ... :D


Now .. am facing a problems with multi-boot  >> when I turn-on my PC .. the boot-loader never asks me what OS I want to load , and it just directly boot UBUNTU9.04 .. if am not fast enough to press (Esc) button in 2 seconds ..
and if pressed it .. I see  booting options 


I want my old configs back please .. with the old 10 seconds waiting time .. I really miss that :(

notice that : am using UBUNTU9.04 & windows XP


any one help :confused:

thnx
[/SIZE][/COLOR][/COLOR]

---

### Post by biebel on 2009-09-13
from a terminal:
```

sudo gedit /boot/grub/menu.lst

```
edit the following lines:
> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

Change the timeout to 10

and
> 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

put a # before the hiddenmenu

Now you will see your list for 10 seconds before it boots to the default one.

---

### Post by drs305 on 2009-09-13
StartUp-Manager if you don't want to manually edit the file yourself. Lots of menu tweaks, especially for Grub 1. Here's a guide:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by mustafa2osman on 2009-09-14
> **biebel said:**
> from a terminal:
```

sudo gedit /boot/grub/menu.lst

```edit the following lines:

Change the timeout to 10

and

put a # before the hiddenmenu

Now you will see your list for 10 seconds before it boots to the default one.

thnx 4 help ... but .. could u just explain it ,,, am kinda new to UBUNTU

---

### Post by drs305 on 2009-09-14
I recommend StartUp-Manager but if you want to manually edit your menu.lst:
Open a terminal: Applications Menu, Accessories, Terminal.
Open menu.lst with a text editor, with adminstrative rights:
```

gksudo gedit /boot/grub/menu.lst
```
You will be asked for a password. Type your's in and ENTER.
The follow the instructions in Post #2. 
The two lines you edit should end up like this:
> 
timeout 10
*and farther down*
# hiddenmenu

10 is a 10 second delay. Change the value to whatever delay you want.

Save the file after you have made the changes.
Reboot.

---

### Post by mustafa2osman on 2009-09-14
> **drs305 said:**
> StartUp-Manager if you don't want to manually edit the file yourself. Lots of menu tweaks, especially for Grub 1. Here's a guide:
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)


THNX ... i did install start-up manager 3 days ago .. but after i messed up with grub >> the manager no longer working :(

---

