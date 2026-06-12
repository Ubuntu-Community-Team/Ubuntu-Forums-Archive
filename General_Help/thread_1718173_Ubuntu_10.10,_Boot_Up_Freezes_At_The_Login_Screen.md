---
title: "Ubuntu 10.10, Boot Up Freezes At The Login Screen"
date: 2011-03-30
forum: General Help
---

### Post by BriniaSona on 2011-03-30
i start up the computer, it loads, it arrives to a screen that says the laptops name, and a bar at the bottum. I can interact with this bar, it is blank and has a picture of a little man with a circle. Clicking on this does nothing, another says shutdown and reset, again clicking on it does nothing. I think the error occured when the computer got unplugged while updating.

now before we get into all this GRUB and fancy stuff. I am completely new to linux. I installed this using a cd made from an iso image downloaded from the site. I did not use a windows loader. I don't even have windows anymore. I have all my personal information and data on here and would like it to be restored.

I googled it and it says to go to recovery mode using GRUB, don't know how and don't know what grub is.:confused::confused::confused::confused::confused:

---

### Post by cain071546 on 2011-03-30
ok when you first boot your computer GRUB (which is a Graphical boot loader meaning it takes Operating systems/if there are multiples and shows a nice little menu for you to choose one) 

Now you said that Ubuntu/Linux is all you have on the PC
So your GRUB Menu is most likely hidden.

When you first turn on your computer wait until you see a little blinking cursor at the top of screen normally the left hand side just before you start seeing Ubuntu try to boot, when you see that cursor press any key
like Enter or Space it should load a little menu

now use your arrow keys to navigate down the List until you highlight the entry 
thats says Recovery Mode

now if all goes well it will bring you to a command line were you can log in

after loging in your still at a command line now you want to start X by typing in "startx" - no quotation marks 

or "sudo /etc/init.d/gdm start"  you may need to start X first I don't really know i don't login this way very often

even if Gnome is damager or missing you can at least sudo apt-get
and reinstall or remove anything that you need to

as long as you can get to a command line all hope is not lost 


i assume you posted this question from a working PC so try these links

[http://tombuntu.com/index.php/2008/02/08/starting-and-stopping-](http://tombuntu.com/index.php/2008/02/08/starting-and-stopping-)
gnome-from-the-command-line/

[http://ubuntuforums.org/showthread.php?t=155442](http://ubuntuforums.org/showthread.php?t=155442)

[http://ubuntuforums.org/showthread.php?t=978882](http://ubuntuforums.org/showthread.php?t=978882)

I really hope that this helps 
just don't give up Linux is always worth the trouble

---

### Post by Hedgehog1 on 2011-03-31
You can also boot of the LiveCD/LiveUSB, select 'TRY' and then copy your data from the computer to a USB stick or USB drive.

If you want to try to save your install, please do this from the LiveCD/LiveUSB:


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

---

### Post by agupta312 on 2011-04-03
can i do the same to launch netbook edition?

---

