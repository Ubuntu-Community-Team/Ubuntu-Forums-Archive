---
title: "New to Linux!  Need all the help you can give! No Cursor Among Others!"
date: 2011-07-18
forum: General Help
---

### Post by Lestathim on 2011-07-18
I recently started to experiment with Linux and decided to install Ubuntu.  Now be mindful that I have absolutely zero experience with any other OS except Windows.  So after successfully installing Ubuntu onto a second hard drive and booting up the OS I have ran into a wide array of problems.  The most important in my mind is  having no mouse cursor.  The mouse works fine and I can click on icons and what not but I have absolutely no cursor.  I have been improvising and using keyboard commands to make my way around the OS.  The mouse I have is the Razer DeathAdder 3500. Now I'm not sure what other information one might need to help fix this problem but I will include my full system specs below.  If anyone has any idea on how to use make this work or how I could get a display I would be forever grateful.

The second problem that is occurring happens when I open up any type of window on the system.  Sometimes whenever I open up a window it'll go completely black like I highlighted the entire contents of the window. it won't be a solid black either it'll be like a scrambled black with sections of white and other colors inside.  Looks like some sort of glitch.  This also occurs on the desktop as well.  At the very top of the screen I will have a line of this weird glitchy stuff above the top menu bar.  The monitor I have is an LG Flattron LCD W2453V.  Also the video card I have is an Asus EAH5830.

As I said before I have absolutely no experience with Linux whatsoever but I am completely fascinated by open source software and want to know more.  If anyone would like to lend a helping handing to this and explain to me what needs to be done I would greatly appreciate it !

Thanks!

---

### Post by JC Cheloven on 2011-07-18
Hi, and welcome to the forums!

You have an unusually bad experience with linux. I think I never heard about a mouse with no cursor. But probably there's nothing wrong with your mouse, and everything is caused by the graphics card. 

This leads to the second (and possibly only) problem: something related to the Asus EAH5830 or its driver. As a start point you could open "hardware drivers" from the administration menu, and see what's here. 

Also if you can open a terminal (accesories menu) and run these commands, we can see which hardware components you have (from the terminal select with the mouse if you can, and use the menu to copy; paste back here):
```
lspci
```
```
lsusb
```

---

### Post by JC Cheloven on 2011-07-18
I see [here]("http://uk.asus.com/Graphics_Cards/AMD_Series/EAH5830_DirectCU2DIS1GD5/#specifications") that the graphics engine of your video card is ATI Radeon HD 5830, so it's probably recognized as such by the system. I guess it should work with the catalyst driver. The "hardware drivers" application should take care of that. Please run it as mentioned above.

---

### Post by Lestathim on 2011-07-18
First off thank you so much for trying to help me out I really appreciate it.  With that said, where exactly is the accessories menu and the administrative menu.  I apologize for not having much of a clue but I'm doing my best to follow.  Also, where do I enter the code that you provided at?

---

### Post by OldBoy44 on 2011-07-18
Applications - Accessories - Terminal - :)

---

### Post by Blasphemist on 2011-07-18
If you're on 11.04, press the "windows" or super key and start keying additional drivers. As soon as additional drivers is the first application (after I type the ad but your search may not be as efficient immediately) press enter.

---

### Post by Lestathim on 2011-07-18
Thanks everyone for all of your help.  The problem was with the video card driver.  I can't recall exactly what it said but I went into the hardware section and it said it was a 3rd party driver that needed to be installed.  The driver was an ATI driver as mentioned above.  Upon picking to install I had to "authenticate" the download with my admin password and then restart the system.  Once the system was booted the mouse cursor was visible and all graphical glitches fixed.  Thanks again everyone for all the help.  I am very glad with this kind of support that I have decided to switch to Ubuntu.

---

### Post by Swagman on 2011-07-19
I know your problem has been solved but in future, to get a terminal, just press the following key sequence

ctrl + alt + t

---

### Post by JC Cheloven on 2011-07-19
> **Lestathim said:**
> Thanks everyone for all of your help.  The problem was with the video card driver.  I can't recall exactly what it said but I went into the hardware section and it said it was a 3rd party driver that needed to be installed.  The driver was an ATI driver as mentioned above.  Upon picking to install I had to "authenticate" the download with my admin password and then restart the system.  Once the system was booted the mouse cursor was visible and all graphical glitches fixed.  Thanks again everyone for all the help.  I am very glad with this kind of support that I have decided to switch to Ubuntu.

Glad you got it solved with the first pointing (it's easier that way). It's how the "hardware drivers" utility is supposed to work anyway :)

I encourage you to experiment as much as you can, it's the way to get used to the system. And in the event you really break something, reinstalling is both easy and cheap! But keep your data aside in a safe place, of course. Linux is not windows (sure), but this not mean more difficult to use. Only, people comes with a long run under win2, it's a matter of habit.

You should know that you come in at a moment of changes in the linux desktop. The traditional Gnome2 desktop has just evolved to Gnome3, and Ubuntu has just pushed his Unity desktop (which I realize now you're probably using, that's why you didn't find at first sight my indications). Things may not be as polished as they use to be, but as I like to say: "it will improve if we use it".

Apologies for the off-topic welcome speech :)
Best
JC
______________

---

### Post by Lestathim on 2011-07-19
I loved the speech haha no apologizes needed.  Any information to me is good information and what I"m learning from Linux is certainly worth the time I'm putting into it.  I'm glad you guys directed me to the terminal and I've actually been experimenting trying to figure out a few things here and there.  I'm reading a book called Linux for dummies that covers both Ubuntu and Fedora..  The guy that wrote it is doing a very good job and helping the reader understand and follow along.  I'm at a part currently where he's tlaing about experimenting with the terminal.  The writer mentions typing 1s is supposed to bring up all the files in a requested location.  I"m not exactly sure what he means by this or how to do it.  For instance I'll type /etc and it'll say this is a known directory but then if I type 1s it says no such command?  Any idea what I am doing wrong or what I should be doing?

Thanks again!

---

### Post by Bleak888 on 2011-07-19
to move to various directories requires the cd command. 

in your example to access the /etc directory, you would use the command 

cd /etc


viewing contents in a directory requires the ls command (that's 'l' as in larry)

so if I want to view the contents in the /etc directory i would type:

ls 

i usually use ls -l for more details. 

Here is a good link that explains that command and you can browse for others:

[http://www.computerhope.com/unix/ucd.htm](http://www.computerhope.com/unix/ucd.htm)

good luck!

---

### Post by JC Cheloven on 2011-07-19
> **Lestathim said:**
> I loved the speech haha no apologizes needed.  Any information to me is good information and what I"m learning from Linux is certainly worth the time I'm putting into it.  I'm glad you guys directed me to the terminal and I've actually been experimenting trying to figure out a few things here and there.  I'm reading a book called Linux for dummies that covers both Ubuntu and Fedora..  The guy that wrote it is doing a very good job and helping the reader understand and follow along.  I'm at a part currently where he's tlaing about experimenting with the terminal.  The writer mentions typing 1s is supposed to bring up all the files in a requested location.  I"m not exactly sure what he means by this or how to do it.  For instance I'll type /etc and it'll say this is a known directory but then if I type 1s it says no such command?  Any idea what I am doing wrong or what I should be doing?

Thanks again!
It's "ls" first and 3rd letters of "list" (the former isn't the number "1"). 
BTW, it is customary over here to mark the thread as solved when it is, so that other people can do more effective searches. Look at the red link "thread tools" at the top of the page.

Hope you carry on enjoying the free world :)

---

