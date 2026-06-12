---
title: "Which 'ATI'  should be installed?"
date: 2009-07-07
forum: General Help
---

### Post by DougieFresh4U on 2009-07-07
I have an onboard ATI Radeon 3200 HD.
I am re-wording this as maybe my question is causing confusion.
There are 8 maybe more choices for 'ATI' driver selection in Synaptic.
Out of those choices, which drivers should be selected to function with my graphics card? 
I know that all those installed cannot be the correct ones, some of those should be uninstalled and I would like to know which ones.
Thanks

---

### Post by karrank% on 2009-07-07
Have a board with this chipset and love it--I just enabled the frglx driver in system>admin>hardware drivers. Not doing anything special tho, browsing, youtube, etc, it supports dual-screen tech thru catalyst Applications>add/remove)

Works great under Hardy.

---

### Post by akakingess on 2009-07-07
The only (2) that I have installed are:

xserver-xorg-video-ati & xserver-xorg-video-radeon 

and my laptop runs everything fine with onboard video, flash, youtube, etc.  I don't know if any of the others are actually neccessary or if they are slowing anything down, though, either.

---

### Post by DougieFresh4U on 2009-07-07
I have re-worded my question to help make it a little better to understand what I am trying to do. Please re-read my origanal post
Thanks

---

### Post by akakingess on 2009-07-07
> **DougieFresh4U said:**
> I have re-worded my question to help make it a little better to understand what I am trying to do. Please re-read my origanal post
Thanks


Thanks for the rewording, but I don't think it changes my anwer at all. I would uninstall all except for:

xserver-xorg-video-ati
xserver-xorg-video-radeon

Then, if you seem to lose some control/functionality that you had before, begin installing 1 at a time until you find the one that improves your card, and uninstall those before it. I hope that made sense, if not please feel free to IM me either here or AIM, ICQ, or MSN.  All my contact info is available in my profile.

---

### Post by karrank% on 2009-07-08
I humbly and freely share what little knowledge I have of this situation and what worked for me; I possess a system with an ATI Radeon HD3200: It works quite well when I go into System>Administration>Hardware Drivers and enable the proprietary ATI drivers under Hardy. Perhaps it's entirely different for your hardware and OS, configuration, &c.

---

### Post by 3rdalbum on 2009-07-08
Get rid of the "debugging symbols" packages, if you needed them you'd know what they were :-)  (they're for programmers who are debugging the driver)

Are you having some specific trouble with your system?

---

### Post by DougieFresh4U on 2009-07-08
> **3rdalbum said:**
> 

Are you having some specific trouble with your system?

Thanks for your reply.
To answer your question, my Jaunty install is great using 'fglrx'.
My Karmic (yes, I know it's 'alpha' blah blah blah blah) install, I would like to know which of the selected driver is the 'proper' one to be using, as 'fglrx' is not usable at the moment.  Also, the selected drivers in Synaptic say nothing 'ATI Radeon 3200 HD specific'  so I would like to have a better understanding of what category my card falls into with the Synaptic options.
I hope I have made my question clear??

---

### Post by carml on 2009-07-08
There's something under System->Administration->Hardware Driver? Maybe there the option there to install the correct proprietary driver.

---

### Post by dstarzfn72 on 2009-07-08
I have the same card in my HP laptop. All I did to get it working right was go to Applications-->System-->Hardware Drivers and selected it. The window that pops up will show the ATI card and that it is not active. Just select it and click activate. It should ask for your password and after you enter it it will activate the card. Just restart and go back to the Hardware Drivers and see that it should now be green and show active and in use.

---

### Post by DougieFresh4U on 2009-07-08
> **dstarzfn72 said:**
> I have the same card in my HP laptop. All I did to get it working right was go to Applications-->System-->Hardware Drivers and selected it. The window that pops up will show the ATI card and that it is not active. Just select it and click activate. It should ask for your password and after you enter it it will activate the card. Just restart and go back to the Hardware Drivers and see that it should now be green and show active and in use.

Thanks for your input. 
However, I did state in my post all is good with my Jaunty install with the 'hardware driver' selection.
Is there some reason why I can not get a 'direct' answer for my question for my Karmic install (not posting this in Karmic as it's not a development issue)
**In 'Synaptic" which one of the ATI drivers in the 'xserver' section should I be using for 'ATI Radeon 3200 HD. I am aware that 'Hardware Driver' from the 'Preference' menu will not work at this time**

---

