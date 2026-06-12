---
title: "Black, frozen screen after booting up."
date: 2010-03-15
forum: General Help
---

### Post by asuastrophysics on 2010-03-15
Hey guys,

I'm at a complete loss here. If I choose to boot Ubuntu, the splash screen appears, but right when the login screen should appear, I get nothing. 

This is how it started:

While update manager was installing updates, I hit ALT+F2 to get to the TTY. I did this because ubuntu now refuses to mount any usb devices whatsoever.
(for more on that, see this link: [http://ubuntuforums.org/showthread.php?p=8973348](http://ubuntuforums.org/showthread.php?p=8973348))

Once I got to TTY3 or whatever, I hit ALT + F7 to get back to the GUI. All I got was a black screen and a mouse. The computer froze and I restarted. All I have now after booting is a black, frozen screen. ALT + any F key to get to TTY doesn't work.

I really don't know what to do here. Can somebody help me through the recovery mode?

---

### Post by asuastrophysics on 2010-03-15
bump

sorry, this problem is becoming a horrible nightmare. I've been trying to fix it for the past 3 hours. I switched my ati radeon 2400 hd pro out for an nvidia card and it booted up just fine.

how do i remove all the graphics drivers for this ati card, so that it boots into "safe graphics mode"?

I tried sudo apt-get remove xorg-driver-fglrx, but it said that "it wasn't installed". 
Is there a driver folder that I can get into to just delete the thing?

Thanks

---

### Post by asuastrophysics on 2010-03-15
update: solved.

So if anyone else ever happens to hit CTRL + ALT + F key for TTY while updating, and you own an ATI card, prepare for linux to just quit and lock up for no reason.

the only way to fix this problem is to:
1. Turn off your computer + disconnect power 
2. Rip out the ati card
3. Put in an nvidia card (because everyone just happens to have a spare card laying around their house)
4. Boot it up again
5. Download new ATI drivers from their website (Do NOT go to ubuntu documentation for this. It is completely useless and will not fix the problem)
6. Run the .run file with a "sh" command. 
7. Install new drivers + turn off computer
8. Rip out the nvidia card + replace it with the ati
9. boot it up. your finished. 

what a stupid bug. usability and stability FTW!

---

