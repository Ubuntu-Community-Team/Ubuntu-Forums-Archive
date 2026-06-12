---
title: "ubuntu is not runnning"
date: 2009-08-12
forum: General Help
---

### Post by sahilsonu on 2009-08-12
_**UNABLE TO BOOT UBUNTU OS**_

Hello guys,
I installed a video drive in my ubuntu 9.04 edition.
ATI DRIVER
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

sudo aticonfig -initial


sudo aticonfig -overlay-type=Xv
.........and then   i install another driver ..whch i forget....its name start with "E"..a short name which resemble "elgy" .

But when i restarted it...all the pixel get distorted, nothing is visible beside some colored lines....jst a like a spectra of colors.

will anyone  bother to tell me how to make my "ubuntu Os" work as b4.

---

### Post by rajeev1204 on 2009-08-12
Go to main menu>system>adminstration>hardware drivers and install or reinstall ati driver from there.Then press Alt-SysRq-K which will restart your Xserver.

See if that helps.

---

### Post by sahilsonu on 2009-08-14
This can be done once i get a chance to log in to desktop.
But , here is i m facing difficulty.

I got no display i run the ubuntu ,,,,jst a coloured spectra covering the whole screen....nothing visible.

Somebody told me ....i need to boot the boot the ubuntu in command prompt mode so that u cna uninstall it there.........by using command.

would somebody tell me how to do that...and commands too.
It'll be great help.:(

---

### Post by P4man on 2009-08-14
does 

sudo apt-get remove xorg-driver-fglrx

work?

Is it possible you have an older ATI card no longer supported by the (binary) ati drivers?

---

### Post by gnuvistawouldbecool on 2009-08-14
When you're system starts, change to the recovery mode boot option in grub, then you should get a root terminal.

You could then try a "startx" command, and when it doesn't work, find out if it gives any error messages.

I don't know of any other driver apart from the fglrx for ati, so thats about all i can say.

---

### Post by sahilsonu on 2009-08-14
B4 that will anyone tell me ..how to enter in command promp or console, and how to get out of it too so that i can try to unintall that driver.
i am a novice linux user.:(

---

### Post by bchurchill on 2009-08-14
> **sahilsonu said:**
> B4 that will anyone tell me ..how to enter in command promp or console, and how to get out of it too so that i can try to unintall that driver.
i am a novice linux user.:(

Do exactly as [gnuvistawouldbecool]("http://ubuntuforums.org/member.php?u=623086") suggested: when you boot up you'll be able to enter recovery mode.  If you have grub (most likely the case), there will be a menu of options to choose from.  Otherwise you may need to press a key combination to get to it.  Just restart your computer, and look for any options it gives you to go into recovery mode as it boots up.  Then follow the others' instructions on starting xserver from the command line in recovery mode.

---

### Post by P4man on 2009-08-14
if you only have ubuntu installed, you may have to press Escape during grub to see the menu. grub loads right after your computer started, so after the bios and before you get the ubuntu logo loading screen.

Another way is letting it boot as usual, when you get the distorted screen, press control+alt+F1 to get a full screen terminal.

---

### Post by 3rdalbum on 2009-08-14
For future reference, the recommended way of installing the ATI driver is to go to System > Administration > Hardware Drivers. If your card is not suitable for the official ATI driver, then the Hardware Drivers program will not offer it.

---

### Post by sahilsonu on 2009-08-14
Hurraayyyyyyyyyyyyyyyyy......................:P

Thanks to all for such a invaluable help otherwise i was going to reinstall Ubunt.

first i start the computer normally, boot into ubuntu normal mode....and when the screen distort   i press ctrl+alt+F1........bt nothing happen

then,

I  restart the computer and went to ubuntu recovery mode, then i press "enter " on  a option there " go to shell promp"  and there i type 

sudo apt-get remove xorg-driver-fglrx

and then i boot into ubuntu .......without any further problem.:):guitar::lolflag::-({|=

---

