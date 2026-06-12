---
title: "Going back to 10.04"
date: 2011-03-07
forum: General Help
---

### Post by daddy0h on 2011-03-07
OK... I gave 10.10 a try and I am having issues that unfortunately are rendering the OS inoperable. I would like to give 10.04 a try, thinking it will be more stable. Can I install 10.04 over 10.10... and if so... how do I do it so that I do not muck up the loader?

---

### Post by mikewhatever on 2011-03-07
Do you want to preserve the old bootloader?  Why?

---

### Post by daddy0h on 2011-03-07
oh... well... this is what i have seen when doing multiple boots... every time you make a change on the operating systems that are installed, the loader shows ALL the options EVER available; present, past, etc... so, what I am afraid of is that i will install 10.04 and then the bootloader will read Win XP and then all the options for 10.10 AND then all the options for 10.04... choices are good... but that's too many!!!!

---

### Post by mikewhatever on 2011-03-07
When several OSs are installed, is it not beneficial to be able to boot them? Why install an OS that you can't boot?
When Ubuntu gets installed, the installer searches for all other installed OSs and adds them to the boot menu.
I'd also suggest testing before installing. Run it from a CD/USB for an hour or two, see what works and what doesn't.

---

### Post by daddy0h on 2011-03-08
ok... look... the point of this thread is not whether to keep the installer or not... ithe point is how to uninstall the 10.10 version so i can go to 10.04 and erase the loader so i don't have the multiple versions of ubuntu, just the 10.04... that is what i am asking... but you know what... since you are asking... the reason why i want to go back to 10.04 is because the mouse is not working properly.... i have a logitech trackball and the oddest thing is happening... i start using the system and then the mouse, even though it can move around, cannot click... i mean, i can click but i cannot select, drag, anything with the mouse... it actually looks like the mouse is too weak... i can see it "select" an item but i cannot get a response from a click... any ideas? also... don't get too technical on me... this is my first foray into the Ubuntu side of the street.
I have done 2 reinstalls and it does the same thing.
thanks

---

### Post by ankspo71 on 2011-03-08
Hi,
When we need to remove an existing Ubuntu installation so we can downgrade to another version of Ubuntu, we have no choice but to choose the manual partitioning option so we can manually replace (or reformat) the existing Ubuntu partition(s). Otherwise, if we let the Ubuntu installer automatically divide up and format the drive for us, it assumes we want to keep the previous installation too, which leaves us with more than one Ubuntu.

By the way, when you select the manual partitioning option, Don't click on the "new partition table" button though, because that will wipe out your Windows installation too. 

Hope this helps.

---

### Post by Hedgehog1 on 2011-03-09
> **daddy0h said:**
> OK... I gave 10.10 a try and I am having issues that unfortunately are rendering the OS inoperable. I would like to give 10.04 a try, thinking it will be more stable. Can I install 10.04 over 10.10... and if so... how do I do it so that I do not muck up the loader?

Do you still need guidance to overwrite a 10.04 on your 10.10 install?  ***ankspo71*** description is correct, but may not be clear to newer Ubuntu users.

If so, please let us know and we can get you rolling.

***The Hedge***

---

### Post by daddy0h on 2011-03-09
Zoings!!! I did re-install Ubuntu 10.10 a third time and this is what i found out (By the way... i was able to take care of the loader issue... no problem... thanks)
A brief history: I installed 10.10 and all was well for a few days when all of a sudden my mouse stopped responding... kind of... I was able to move it but if i clicked on an item, Ubuntu would not register the click, therefore i was not able to select, execute, drag, etc with the mouse. The mouse is a wireless trackball by Logitech. It has a receiver for both the keyboard and mouse that has a cable that connects to a USB port.

 After numerous tries i thought to replace my WIRELESS mouse with a wired mouse... I installed the wired mouse before i removed the wireless because the receiver for the wireless also carries the keyboard... on a whim i decided to test the wireless mouse and... Shazam... it now works... but i have to have a wired mouse (PS2) attached to the computer.
This tells me that there might be something wrong with the USB driver... or whatever controls the USB, or the mouse.

What do you recommend I do to fix either the USB or the mouse?
I tend to point the finger at the USB because the mouse works well in Windoze XP... I also installed SuSe 10.0 and it worked properly... so the fault lies within UBUNTU and the USB.

Your turn...

---

