---
title: "HELP!  Won't boot after I replaced latest GDM with GDM  2.2!"
date: 2009-12-12
forum: General Help
---

### Post by vinay427 on 2009-12-12
Hi,

I wanted to change the login theme of 9.10 today and found a [thread here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8413578") (last post) where it said to uninstall the pre-installed GDM and replace it with 2.2.  I did that, and now my computer won't boot completely.  First it says "GRUB Loading..." which is normal then the Ubuntu logo, also normal.  However, after this it just displays a blinking cursor.

I thought GDM was just a graphical interface and that if it was uninstalled you could simply login through the terminal.  However, Alt+Ctrl+F1 and Alt+F7 did nothing.

Also (maybe this could help) I saw another post to change the theme(not on these forums) that said to log out and press Alt+Ctrl+F1 to go to a terminal where you could log in and perform commands.  I never got that when I pressed Alt+Ctrl+F1.  Instead I had gotten the same blinking cursor but that time Alt+F7 brought me back to the graphical login screen.

So does anybody know what to do?  I *could* restore because I don't have anything very important but it would obviously be a huge hassle.

The OS:
Ubuntu 9.10 Karmic Koala 64-bit Desktop Edition

Thanks,
vinay427

---

### Post by 23dornot23d on 2009-12-12
When you boot up you should have a option to start up a Failsafe session

When it gets to a MENU ..... choose the option for Teminal and Network

_________________

then enter 

sudo apt-get update

then enter

sudo apt-get install gdm

just let it complete and try a normal login 

_________________

If it gives you the choice to choose the Display manager choose gdm2.20

I have not done this for a while ..... if someone wants to confirm

or give better instructions please add another comment after this one ....

____________________________________________________________

[ best I can do .... possibly ( sudo startx ) .... is possibly another option 

 only try this if the above fails to get you into a Graphical Display .... ]

once you get the Display back - you should be able to use Synaptic .... again ....

Let me know what happens ....

---

### Post by vinay427 on 2009-12-13
> **23dornot23d said:**
> When you boot up you should have a option to start up a Failsafe session

When it gets to a MENU ..... choose the option for Teminal and Network

_________________

then enter 

sudo apt-get update

then enter

sudo apt-get install gdm

just let it complete and try a normal login 

_________________

If it gives you the choice to choose the Display manager choose gdm2.0

I have not done this for a while ..... if someone wants to confirm

or give better instructions please add another comment after this one ....

____________________________________________________________

[ best I can do .... possibly ( sudo startx ) .... is possibly another option 

 only try this if the above fails to get you into a Graphical Display .... ]

once you get the Display back - you should be able to use Synaptic .... again ....

Let me know what happens ....

Thanks, but I can't see an option for a failsafe session.  I used to before on the normal GDM but now it just loads GRUB, shows the Ubuntu logo, and then the blinking cursor screen comes.

---

### Post by wojox on 2009-12-13
Try holding down the <Shift> key after bios.

---

### Post by vinay427 on 2009-12-13
> **wojox said:**
> Try holding down the <Shift> key after bios.

Ok, when I do tha it shows 4 different versions of Ubuntu, two ending with a 14 and two with 15.  There is also two Memory Test choices.  I tried all 4 Ubuntu choices and they don't do anything except just stay at a sort of loading screen.

---

### Post by vinay427 on 2009-12-14
> **vinay427 said:**
> Ok, when I do tha it shows 4 different versions of Ubuntu, two ending with a 14 and two with 15.  There is also two Memory Test choices.  I tried all 4 Ubuntu choices and they don't do anything except just stay at a sort of loading screen.

Nevermind, I couldn't really wait for a solution and just restored.  Only takes like 30 minutes anyway!

If anyone has a solution, feel free to post it anyway.  It might help someone with the same problem!

---

