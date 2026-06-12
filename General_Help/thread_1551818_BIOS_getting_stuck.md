---
title: "BIOS getting stuck"
date: 2010-08-12
forum: General Help
---

### Post by nick85 on 2010-08-12
I tried the Ubuntu CD without making any changes to the system. But in order to do that I changed my BIOS settings to boot from CD instead of the choice which was floppy. Unfortunately I forgot the Ubuntu CD was 64 bit (i have another 64 bit machine that runs Ubuntu) even though the system was 32 bit. facepalm...

While trying to boot from the CD i remembered that it was a 32 bit system so i rebooted it and took out the disk. Now here's the problem. The computer starts up and it gets to a screen which says:

Platinum BIOS (pretty black and white picture)
Press <Tab> to switch to Post or <DEL> to run BIOS setup

and previously i was able to press the "Delete" key and it would take me to the BIOS settings but now it's just frozen on that screen. I have tried all the keys "delete" "F8" "F9" "F10" "ESC" "Tab" etc but nothing works. It's just stuck. 

Any help would be very very appreciated.

---

### Post by Woody1987 on 2010-08-12
If you have access to your motherboard manual, it should tell you how to reset the bios.

---

### Post by nick85 on 2010-08-12
thank you for responding. i can't seem to find the manual but i pressed the clear cmos button for several seconds and took the battery out for a minute but it's still stuck on that screen

---

### Post by Elmer Fudd on 2010-08-13
What is your hardware.
Computer/motherboard/BIOS make and rev or version.

Also- when you get to the BIOS screen and it appears to lock up, will the capslock or numlock keys toggle properly.

---

### Post by dino99 on 2010-08-13
as you have reset the cmos, i only see the keyboard to blame: clean it (key damage or dusty)

---

### Post by nick85 on 2010-08-13
It's a K8N Neo4 Platinum/SLI motherboard 
2 gigs of ram 
nvidia card
amd chip
it's got a printer and a scanner hooked up to it
and the Bios chip is a Phoenix BIOS B688 1998 but the splash screen says Platinum

no "Caps Lock" doesn't work. it's a usb keyboard. all the lights flash on and off when the computer turns on but then they go off after that. "Num Lock" "Scroll Lock" are also unresponsive.

i tried it again this morning and the splash screen doesn't even pop up. nothing. the screen button turns orange instead of green saying that it's not getting any signal

i tried another keyboard again but not the usb kind (PS/2)

i made sure the vga cord is connected properly and it is but i'm not getting anything

---

### Post by DeMus on 2010-08-13
> **nick85 said:**
> thank you for responding. i can't seem to find the manual but i pressed the clear cmos button for several seconds and took the battery out for a minute but it's still stuck on that screen

Did you also unplugged the mains cord at that time?

---

### Post by nick85 on 2010-08-13
well i turned the button on the power supply from I to O
but i tried it once with it on
could that have killed it?

---

### Post by DeMus on 2010-08-13
> **nick85 said:**
> well i turned the button on the power supply from I to O
but i tried it once with it on
could that have killed it?

Even when you have switched the PC of, parts of it still have power. Take of the mains cord, take out the battery and wait for a while, then reset it.
The reset-switch is it a pulse switch which comes back to the original position when you release it, or does it stay in either position you put it in?
It could be the switch has to be operated for a longer period of time.

---

### Post by nick85 on 2010-08-13
it's a button which becomes unpressed when you release it. when do i press that and for long (approximatively)?

---

### Post by DeMus on 2010-08-13
> **nick85 said:**
> it's a button which becomes unpressed when you release it. when do i press that and for long (approximatively)?

The right order is:
unplug the mains cord
remove the battery
push the switch

Do you have the manual for your motherboard? Maybe it's in there how long you have to keep it pressed.
I have a motherboard where I can change the position of a small plug, I do that for several minutes to make sure all the power is gone and the reset function really works.

---

### Post by nick85 on 2010-08-13
i unplugged it
took the battery out for half an hour
reinserted the battery
pressed the cmos button for 15 seconds
plugged it in
nothing at all. screen won't turn on. no splash screen :(

---

### Post by nick85 on 2010-08-13
am i supposed to press the cmos button when the battery is out? i'll look for my motherboard manual in the meantime

---

### Post by DeMus on 2010-08-13
> **nick85 said:**
> am i supposed to press the cmos button when the battery is out? i'll look for my motherboard manual in the meantime

Yes, push the switch when the battery is out, otherwise the BIOS chip still has power.

---

### Post by nick85 on 2010-08-13
ok i found the manual and did everything it said. 

i don't know if it worked because my screen isn't showing anything... (orange color instead of green)

---

### Post by egalvan on 2010-08-13
> **DeMus said:**
> Yes, push the switch when the battery is out, otherwise the BIOS chip still has power.

With the mains un-plugged and the battery taken out,
the CMOS  has no source of power...

Residual charges on the caps will bleed down in a few minutes.


If I had this machine on my bench...

I would remove/un-plug  EVERYTHING that is not essential to booting..
Drives can stay installed, but un-plug power and data cables.
all extension cards should be removed (leave video if needed)
disconnect the power supply cables going to the mother-board.

leave only the keyboard, RAM, and video.

come back to it in the morning

plug the power supply cables back on the motherboard
plug in mains, and try booting.

---

### Post by nick85 on 2010-08-15
sorry i had be out for a couple of days. 

i tried what egalvan with no success :(

---

### Post by egalvan on 2010-08-16
> **nick85 said:**
> 
i tried what egalvan with **no success** :(

OK, use the PS/2 (small round connector) keyboard on another machine.
MAKE SURE IT WORKS.
It's possible you have a bad keyboard.
Flex the cord, make sure it doesn't have an intermittent short/break.
MAKE SURE IT WORKS.

If this does not work, I would start thinking about a bork'd BIOS chip.
It's possible, though rare, to "scramble" a CMOS if the boot process is interrupted at just the right spot. 
More likely to happen if you "re-boot" by pulling the mains.


You stated that it originally booted from a floppy.
Try booting with a DOS boot-floppy THAT YOU KNOW IS GOOD.
See if the floppy runs and stops, or if it keeps running, or if it doesn't run at all.

(floppy code is very near the beginning of the boot process)

---

