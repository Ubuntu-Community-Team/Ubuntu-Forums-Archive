---
title: "Computer won't boot after changing host name"
date: 2011-03-16
forum: General Help
---

### Post by mcrne on 2011-03-16
Hello everyone,

I'm very new to Ubuntu and installed it (10.10) just a few days ago on a laptop I got for my girlfriend.

The problem is that she wanted me to change the username and **computer name **that I have set up when installing, which I tried to do.

I followed the instructions on this link to change the computer name/hostname: [http://www.liberiangeek.net/2010/06/how-to-quickly-change-computer-name-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/06/how-to-quickly-change-computer-name-in-ubuntu-10-04-lucid-lynx/)

Obviously I did something terribly wrong, because after trying to restart my computer I couldn't boot it. It freezes immediately after the BIOS screen - just displays a blinking dash in the top left corner.

The same thing happens when i try to boot from a CD (I tried both Ubuntu and Windows 7 CD's. Resetting BIOS to default also did nothing.

Is there a way to fix this?

Thanks.

---

### Post by lithopsian on 2011-03-16
You are well hosed if a Live CD will not boot.  Make sure that your BIOS is set so the first boot device is the CD, or activate your boot order menu to choose CD.

---

### Post by Irony on 2011-03-16
I don't see how changing host and username would affect CD boot ups.

---

### Post by mcrne on 2011-03-16
Hello lithopsian,

Thank you for the reply. I already tried setting the CD as the first boot device but with no luck. I tried using both the Ubuntu CD (which booted just fine when I was first installing Ubuntu) and a Windows 7 CD. No matter what i did in BIOS though it just won't boot.

After a couple of minutes the blinking dash does disappear and an error message appears saying "Reboot  and Select proper Boot device or insert Boot Media" if I remember  correctly. This happens no matter which device I select as a rimary boot device. I'm at work now and will be able to verify the exact error message in a few hours.

*Edit: Irony, just saw your comment* *- the following refers to what you said*

The computer has been running for some time before the hostname change so I cannot guarantee that something else I may have clicked on, updated etc. (which may have seemed logical to me at the time - it was my 1st time ever using Linux) caused this problem.

---

### Post by tordeu on 2011-03-16
If you really booted from the CD and that does not work at all, then there seems to be something completely broken, but it has definitely nothing to do with you changing the hostname/username. This would just be a coincidence and you should contact the shop you bought it from and get a replacement.

If, on the other hand you put in the CD, but did not really boot from it (as lithopsian suggested), then you should really check your boot order. Even though changing the host name should not affect it, just check it to be sure. Or are you sure that the system booted from CD?

Changing the hostname as in the link you provided would definitely not cause any problem like this. And changing the username would not prevent your computer to boot from a CD, no matter which guide/tutorial/how to you use for that.

Can you verify that the computer does actually try to boot from the CD? Because if it really does and still does not work, no matter which CD (Ubuntu, Windows) you put in, I would guess it is not unlikely a hardware problem.

EDIT:

Just read your new comment. But I don't see a way an update or something you have clicked on would prevent booting from a CD if it is set up in BIOS as a primary boot device. 
Can you tell if the laptop tries to access the CD while booting? Does the CD drive make noises/blinks? Try booting from the CD from another computer, to check that it has not bee damanged. Nevertheless, it might just be a hardware problem.

---

### Post by mcrne on 2011-03-16
Hello,

Although I'm new to Linux, I am not a complete novice when it comes to using computers, and I did most definitely set it up to try and boot from the CD. I tried every possible combination in BIOS:

CD 1st, HDD 2nd
HDD 1st, CD 2nd
HDD 1st, disabled 2nd
CD 1st, disabled 2nd

And the outcome was the same every time.

Edit: One thing did just occur to me - after installing Ubuntu, at one  point I did insert a CD with the drivers that came with the computer,  but in the Ubuntu version of Windows Explorer (don't know the proper  term yet :)) it appeared not to have any files on it. It did recognize  the CD name which appeared under it's icon, but after clicking on it the  folder seemed empty.

The CD drive does start spinning the CD when i insert it but stops after a few seconds. I didn't pay attention to the LED (if there even is one). I will check the CD light and try booting from the CD's from my desktop and come back to you with the info in a few hours.

Could it be a combination of two problems - my changing hostname made Ubuntu not boot from HDD, and a hardware problem stopping it from booting from CD?

---

### Post by tordeu on 2011-03-16
I really don't see changing the hostname causing any problems when it comes to booting Ubuntu. And even if something caused that problem, it might in fact be two different problems, because booting from CD should still work. 

If there was a problem with the CD drive, it not displaying any contents might be a symptom, but it could be just a simple mounting problem/glitch as well.

If the CDs are working on a different PC, you could try booting from a USB device if the laptop can do that (new models should) and if you have a USB flash drive, to see if that works. 

On [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) you can display a guide on how to make a bootable USB flash drive with the Ubuntu CD on it.


Is the laptop brand new?

bzw: The "Windows Explorer" is "Nautilus" ;)

---

### Post by mcrne on 2011-03-16
Hello,

Thank you all for the help. After spending all last evening trying to reboot I now got home from work and on the first try Ubuntu launched with no problems at all. I then restarted and tried to boot from CD and again it worked great in the 1st try.

This still doesn't explain what was going on last night, so I'll be doing some testing and if it happens again will definitely take the computer back to the shop - this obviously is not an Ubuntu related problem.

Btw. Yes the laptop is brand new, but that doesn't mean a lot since it's a cheapo computer made for the east european market :) I made the bootable USB drive first when installing Ubuntu but it didn't want to boot so I decided to take the easy way and use a CD.

Thanks for your help once again.

---

### Post by tordeu on 2011-03-16
The reason I was asking if it was a new one is because sometimes there is already something wrong with new hardware and it dies during the first days, often giving you trouble from the first minute.

But I am happy to hear that it worked now and no matter what the problem was, I really hope the problem is "solved" for good and you can enjoy Ubuntu now. :P

---

