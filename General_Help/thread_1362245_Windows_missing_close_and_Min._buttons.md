---
title: "Windows missing close and Min. buttons"
date: 2009-12-22
forum: General Help
---

### Post by Slikgman on 2009-12-22
First I would like to say my 64bit Ubuntu 9.10 from a fresh install was running just fine.
 
I am new to Linux so I need a lot of help. 
 
My problems: 
1. My windows do not have close,min, or max buttons in the top right corner anymore.
2. I can not type in windows I select with the mouse.
3. I did notice I was typing in a Tomboy note that was already on my desktop on startup but was not able to select a new window to type in.
4. Mouse works to select menus on Ubuntu Desktop but thats about it.
 
If I go in to terminal mode I can type just fine.
I was able to open VMware Workstation and load Windows XP an type this post with everything working ok, mouse and Keyboard while in VMwares OS. If mouse pointer slides out of VMware window OS, I still have the same problems with Ubuntu.
 
My problems started after I notice my Compiz "3D windows" effect stop working. My 3D windows was checked but my effect was flat on the desk top during cube rotation. This was working before but it stopped and I had know ideal when it did. So I thought being the newbie I am, I would uninstall compiz and compiz setting manager and the do a install.
 
This is when this problems all started. I never did get that "3D windows" effect working either. (If someone has input on this too please let me know.) 
 
My 1st thought was to reinstall Ubuntu 9.10 but I really want to learn and I don't want to reinstall everytime I hit a wall with a problem. I have been able to fix other little problems like Java pluggins and other stuff by google search but this one is hard to find.
 
I thank this community for all your help in advance :guitar:

---

### Post by Raistlin355 on 2009-12-22
Sounds like the classic "Compiz taking away my title bars problem"  Can you use ALT+F2 to bring up a run box and type ```
 metacity --replace
```?

---

### Post by rcayea on 2009-12-22
I believe you can change this by selecting a different look in the desktop backgrouns/theme/customize section. 

I, too, though have had to tweak compiz before to fix such an issue. I just made my effects go from Extra to Normal.

---

### Post by Raistlin355 on 2009-12-23
> **rcayea said:**
> I believe you can change this by selecting a different look in the desktop backgrouns/theme/customize section. 

I, too, though have had to tweak compiz before to fix such an issue. I just made my effects go from Extra to Normal.

How's that gonna change ANYTHING if the title bars are not even being rendered? Oh and changing the effects from extra to normal, that what my code does that I posted.

@Slikgman it would also be helpful to know what video card you are using.

---

### Post by JoelOl75 on 2009-12-23
Sounds like your video card either isn't setup properly for direct rendering (In a terminal type glxinfo)

Maybe you need to install proprietary drivers?  Until then i'd turn off and compiz desktop effects.

Some video cards are just PIA to get compiz working on, even with the proper drivers installed (Uhummmm ATI) or they work for awhile then lockup the computer.

The matacity --replace command should definatly get the title bars back so then you can goto system/appearance and desktop effects and select none.

---

### Post by Slikgman on 2009-12-23
> **Raistlin355 said:**
> Sounds like the classic "Compiz taking away my title bars problem" Can you use ALT+F2 to bring up a run box and type ```
 metacity --replace
```?
 
Unable to open x display, is the msg returned

---

### Post by Slikgman on 2009-12-23
> **Raistlin355 said:**
> How's that gonna change ANYTHING if the title bars are not even being rendered? Oh and changing the effects from extra to normal, that what my code does that I posted.
 
@Slikgman it would also be helpful to know what video card you are using.
 
 
I have a NVID card "Gigabyte 9500GT" DDR3 512MB...
 
 
Dont forget everything was working just fine....  Compiz was fine until I started changing options and then I made my "3D windows"  stop working.   
Only my UI interface has this problem.  Im using the 195 Nvid driver, I think is what its called.  The newest driver.
 
Thanks again for everyones help, got to go to work will check back later.

---

### Post by Slikgman on 2009-12-24
Metacity --Replaced 
fixed my button problem now how do I get my Extra back so I can use compiz?

---

### Post by Slikgman on 2009-12-24
The strangest thing happen a few min. ago and I thought I should share it with the community.  

My Compiz fusion started working again.  Every time I try to turn on Extra in the Visual effects I would loose my title bar buttons on the right so I left it in the "none" option for visual effects.  I had my top panel in auto hide mode and decided I wanted to keep my eye on the clock so I went to preference and unchecked auto hide. After I did a close I noticed my desktop shortcuts move or I should say shift a little.  So I said to my self, self I wonder if that made a difference in on my visual effect.  I went back to put my visual effects back to extra when I closed the window my button stayed.  I went back to my top panel to see if putting it back to auto hide would change anything and it didn't. Now I am back running my Ubuntu with compiz fusion running.  

My original problem is now my only problem.  My "3D Windows" Effect still does not work.  When I rotate my cube its does not show my open windows spaced away from the cube in 3D.  

Does anyone have a FIX for this last problem.  It did work for the 1st week and I don't know why it stopped.

Thanks for reading this post....:popcorn:

---

