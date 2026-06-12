---
title: "Blank red screen after install."
date: 2012-06-22
forum: General Help
---

### Post by papazulu on 2012-06-22
Hi everyone.  I am not new to linux.  I just successfully installed Scientific Linux on another system.  But this is my first time installing Ubuntu in a few years.  I am using version 12.04.  Everything seemed to be installing just fine but when I ejected disk then restarted computer it boots to a blank red screen.  It's the Ubuntu hazy red with nothing, no cursor, no login field, nothing.

This is my third time attempting to install.  I'm at a complete loss.

---

### Post by papazulu on 2012-06-22
> **papazulu said:**
> Hi everyone.  I am not new to linux.  I just successfully installed Scientific Linux on another system.  But this is my first time installing Ubuntu in a few years.  I am using version 12.04.  Everything seemed to be installing just fine but when I ejected disk then restarted computer it boots to a blank red screen.  It's the Ubuntu hazy red with nothing, no cursor, no login field, nothing.

This is my third time attempting to install.  I'm at a complete loss.

Wow no responses.  I can't be the only person to whom this has happened before.  Perhaps it is something related to my graphics configuration.  I am running an Acer widescreen 23" with Radeon HD 6670.  

So no one has any idea what is going on here?

---

### Post by papazulu on 2012-06-22
> **papazulu said:**
> Hi everyone.  I am not new to linux.  I just successfully installed Scientific Linux on another system.  But this is my first time installing Ubuntu in a few years.  I am using version 12.04.  Everything seemed to be installing just fine but when I ejected disk then restarted computer it boots to a blank red screen.  It's the Ubuntu hazy red with nothing, no cursor, no login field, nothing.

This is my third time attempting to install.  I'm at a complete loss.

HA!! I think I know what the issue is.  It is the damned Radeon drivers.  I remember that being an issue long ago with linux.  Radeon not being natively supported and all.  So you mean to tell me after Ubuntu has been out for more than 7 years that they still haven't resolved this.  Now I have to go get radeon's linux drivers from site and attempt to install them in non-gui mode.  GEEzz not this **** again!

---

### Post by PhantomTurtle on 2012-06-22
You can try nomodeset, which might help you get a GUI. After the bios splash screen, hold down the Shift key and you will get the GRUB menu. Now press "e" to edit the kernel you are going to use, most likely the first on the list. Next go to the line that has quiet splash at the end of it and add nomodeset in front of it. So it will look something like this,
```
nomodeset quiet splash
```
You can try that, also on the Ubuntu splash screen(the purple screen) you can press the delete button to see what is going on in the background.

---

### Post by vidtek on 2012-06-22
> **PhantomTurtle said:**
> You can try nomodeset, which might help you get a GUI. After the bios splash screen, hold down the Shift key and you will get the GRUB menu. Now press "e" to edit the kernel you are going to use, most likely the first on the list. Next go to the line that has quiet splash at the end of it and add nomodeset in front of it. So it will look something like this,
```
nomodeset quiet splash
```
You can try that, also on the Ubuntu splash screen(the purple screen) you can press the delete button to see what is going on in the background.

Try phantom's suggestion first.  
If you're still no go, tell us what display port you're using from the graphics card, and if you have more than 1 display.  I had this with a Nvidia card and couldn't work it out, turned out to be the display card wasn't automatically switching to my hdmi projector o/put after I'd finished installing the o/s with a dvi monitor.  

A cold reboot (power right down and leave a few minutes for all the capacitors to drain in the power supply) sorted it. 
Tony.

---

### Post by papazulu on 2012-06-22
> **vidtek said:**
> Try phantom's suggestion first.  
If you're still no go, tell us what display port you're using from the graphics card, and if you have more than 1 display.  I had this with a Nvidia card and couldn't work it out, turned out to be the display card wasn't automatically switching to my hdmi projector o/put after I'd finished installing the o/s with a dvi monitor.  

A cold reboot (power right down and leave a few minutes for all the capacitors to drain in the power supply) sorted it. 
Tony.

Well, I did manage to boot successfully to failsafe graphics mode.  Tinkered around a bit.  Opened firefox.  Then noticed there was no 'x out' thingy in top right of window.  How odd, I thought.  So i completely uninstalled firefox using purge command and then reinstalled it and still no x-out button.  Not only that, I get a message from Firefox saying "use of back arrow not available" for some reason.  I google this and one solution was to restart computer and it would fix itself.  So I did that and new the "blank red screen" boot problem i was having before has evolved into a purple screen with Ubuntu insignia hang-up.

Please folks, please . . . please tell me this is not the Ubuntu that everybody has been raving about.  You know I honestly don't have time for this %$#t.  The only reason I installed Linux in the first place was because I wanted to learn iPython in its more native environment.  But I really and truly don't have time for this.  I need a friggin Linux distro i can slap on my system and not have to worry about all this bull crap.

This is ridiculous.  Thanks for the responses anyway.  After I cool off for a while I may come back and implement your suggestions.

---

### Post by vidtek on 2012-06-22
Papazulu-

Steady on son, you say the reason for you installing is to get the more native environment.  

You are moving from a rigid closed system such Microsoft O/S's, where manufacturers are obliged to write drivers for their hardware to sell their product or not sell anything, to and open system where volunteers spend their valuable time reverse-engineering drivers for the benefit of us all.

Most manufacturers don't give a toss about providing drivers for Linux, it's as much as they can do to write crappy ones for Windows. 

Everybody tries to assist each other with problems in this community, try to remember that when you're working to a deadline and the system isn't doing what you think it should be doing and your temperature is rising, we've all been there.

Tony

---

### Post by papazulu on 2012-06-22
> **PhantomTurtle said:**
> You can try nomodeset, which might help you get a GUI. After the bios splash screen, hold down the Shift key and you will get the GRUB menu. Now press "e" to edit the kernel you are going to use, most likely the first on the list. Next go to the line that has quiet splash at the end of it and add nomodeset in front of it. So it will look something like this,
```
nomodeset quiet splash
```
You can try that, also on the Ubuntu splash screen(the purple screen) you can press the delete button to see what is going on in the background.

Well that worked.  It allowed me to boot into Ubuntu GUI.  But when I restarted it did the purple screen with Ubuntu logo to the left hang-up thing.  Even pressing delete didn't budge it.  So I cold restarted and went back to grub script and noticed that it had not saved "nomodeset."  I looked for option to save editions but none.  So I reentered it and as before it allowed me to reboot to GUI.  Now I need to figure out how to make it function without manually having to jimmy-rigging it every time I restart computer.

---

### Post by PhantomTurtle on 2012-06-23
> **papazulu said:**
> Well that worked.  It allowed me to boot into Ubuntu GUI.  But when I restarted it did the purple screen with Ubuntu logo to the left hang-up thing.  Even pressing delete didn't budge it.  So I cold restarted and went back to grub script and noticed that it had not saved "nomodeset."  I looked for option to save editions but none.  So I reentered it and as before it allowed me to reboot to GUI.  Now I need to figure out how to make it function without manually having to jimmy-rigging it every time I restart computer.

That is just a temporary option and I would not use it permanently. When you get into Ubuntu, open the Additional Drivers utility(jockey-gtk) and install the AMD drivers, restart and try to get it working. However if you do want to use it then use this guide - [http://mizex.com/categories/open-source/item/how-to-permanently-set-nomodeset]("http://mizex.com/categories/open-source/item/how-to-permanently-set-nomodeset").
> 
Open Terminal and type in,

```
gksudo gedit /etc/default/grub
```

change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"

Save, close, switch to terminal and type in,
```
sudo update-grub
```

---

