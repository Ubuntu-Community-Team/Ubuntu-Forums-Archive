---
title: "Dell 3.4 GX280 wont boot after moving the computer!"
date: 2012-03-19
forum: General Help
---

### Post by doctorlingling on 2012-03-19
Hello, I am brand new to here and have tried some of the suggestions on this forum as well as others online, but to no avail.  My only computer for school will not boot into ubuntu, it was working fine for months.  I moved the computer to a different shelf and now when it goes to boot it just locks me on a black screen.  I burned a copy of a new ubuntu and tried re-installing but this does not work either?  Can any one out there help me out??  - Jim

---

### Post by josephmills on 2012-03-19
Hello there and welcome to the forums.

I am not sure that I Understand what you mean by "moved" to a different shelf. What happens if you hold the **shift** key down well booting? do you get a grub screen ?

---

### Post by doctorlingling on 2012-03-20
Sorry for the confusion, I physically moved the tower from the floor to a shelf. I believe I am able to boot from the cd, as it brings up the main menu to install, check disk etc, but any of those options just result in a totally blank screen.  I only have ubuntu on the hard drive, no other os.  At the first menu, it gives me F6 option to turn off certain parameters( I don't really know what this means) like naopic, expert mode etc.  Do you think the system died on me, and is there anyway to save it?  Thank you for replying so quickly before.

---

### Post by doctorlingling on 2012-03-20
Another thing I forgot to answer from your question, is about the grub menu.  I just tried it, and i got a black screen with boot: at the top left corner with the flashing _ symbol-  Is this good?

I tried typing after the boot:_ but it wont let me type any letters or numbers

---

### Post by oldos2er on 2012-03-20
Did you check the hard disk connections? Sounds like some cables might be loose.

---

### Post by PhantomTurtle on 2012-03-20
When you start your computer and get past the grub screen at the black screen press delete on your keyboard(Press this after you get past your bios and the grub screen). This will show you why it won't work. Also you can try the nomodeset setting in the grub boot menu. When you get to the boot menu press "e" and it will show you the grub options in there replace,

```
quiet splash
```

with

```
nomodeset
```

Hope that helps.

---

### Post by doctorlingling on 2012-03-20
I tried the nonmodeset option, and then chose to install-  the cd drive seemed to keep spinning faster and faster and faster until i unplugged the whole computer to prevent it from exploding-  It did this once before without any changes- anythoughts?  If anyone is near syracuse ny I would be willing to pay someone to fix it for me

---

### Post by PhantomTurtle on 2012-03-20
> **doctorlingling said:**
> I tried the nonmodeset option, and then chose to install-  the cd drive seemed to keep spinning faster and faster and faster until i unplugged the whole computer to prevent it from exploding-  It did this once before without any changes- anythoughts?  If anyone is near syracuse ny I would be willing to pay someone to fix it for me

How long did you leave it on until you unplugged it because if a disc spins faster I think that's just normal.

---

### Post by doctorlingling on 2012-03-20
If you could hear it, you would know the thing was SPINNING wicked fast, - it was a great cheap computer and I dont want to just throw it out.  Since it allows me to boot from cd, but after I choose to install it it just goes blank could that mean its a hard drive problem?

---

### Post by doctorlingling on 2012-03-25
SOrry for the delay, I haven't had a computer to work with for a little while,  I did notice that the loud spinning noise was actually the PSU? fan.  The fan is what kept spining faster and faster.  I thought about trying an install through the network but have no network option on the boot sequence menu.  One thing that got me a little farther was when I chose to "boot from first hard disc", it gave me more options such as ubuntu, with linux 3.0.0-16 generic, same as above but with (recovery mode) previous linux versions, memtest86+, and memtest86+ serial console 115200.  The recovery mode gives me a whole list of things such as PCI interrupt link etc.   unabeled traffic allowed by default, 3 comparators, 64-bit  14.318180 MHz counter- which I do not understand what this means.

---

### Post by PhantomTurtle on 2012-03-25
> **doctorlingling said:**
> SOrry for the delay, I haven't had a computer to work with for a little while,  I did notice that the loud spinning noise was actually the PSU? fan.  The fan is what kept spining faster and faster.  I thought about trying an install through the network but have no network option on the boot sequence menu.  One thing that got me a little farther was when I chose to "boot from first hard disc", it gave me more options such as ubuntu, with linux 3.0.0-16 generic, same as above but with (recovery mode) previous linux versions, memtest86+, and memtest86+ serial console 115200.  The recovery mode gives me a whole list of things such as PCI interrupt link etc.   unabeled traffic allowed by default, 3 comparators, 64-bit  14.318180 MHz counter- which I do not understand what this means.

Since you can get to the grub menu of your existing install you can go into recovery mode and try repair broken packages with dpkg, update grub, or drop to root shell. There should also be a xfix option too which you can try (this option will try to reconfigure your X window system). Also you can drop to the root shell and try to startx(I'm not completely sure how this will work).

---

### Post by doctorlingling on 2012-03-25
Thanks for the reply!  I have tried all of the recovery mode options, there was one off the bat, and then i chose previous linux os and there were two different ones .15 and .12 to chose from .  All three landed me at the same screen with the bunch of information that ended with 3 comparators, 64-bit 14.318180 MHz counter.  Then the flashing _ symbol to which I cannot type anything.  Also, holding down the power button for like 10 seconds does not turn off the system, idk if that means anything.   Does this sound like a hard drive problem, or a more complex issue.  The weirdest thing was is that it was working just fine before hand.  I can replace the hard drive with a new one, but would rather not spend money on it to only have the same problem as I am having now.

---

