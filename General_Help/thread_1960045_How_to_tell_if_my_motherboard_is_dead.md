---
title: "How to tell if my motherboard is dead"
date: 2012-04-16
forum: General Help
---

### Post by xigen on 2012-04-16
Hello,

My linux box is about 5 years old.  Today it went bzzz zzz zzzz and locked up.  Upon reboot it would not boot and I got a message to hit 'delete' for setup or 'tab' for  (*I forgot).

Given that the system has been running quite well for the past 5 years - I suspect that my motherboard has died.

I have tried using a rescue disk as well as a Knoppix disk.  Both do not boot.

My next step is to get compressed air and clean any dust off the components.  

How would you recommend I move forward in figuring out what is broken?

Best,

MW

---

### Post by JC Cheloven on 2012-04-16
It seems you're hardware-prone :)
To clean out dust is a good starting idea.
So, I'd try to discard failure of components, one at a time. 

1) ram (it's the easiest). Try to plugout some bank(s), or try different ones if you've any available.

2) the thing that powers everything (I don't remember the english name for that, sorry). Once, I had similar sympthoms, and fixed it by replacing that.

3) the graphic card... I'd say it's not likely your problem. I'd let that aside for now.

4) maybe the cpu... but probably you don't have one to replace. It's also more tricky. Personally, if my cpu fails, my path would be to pick up usable components and to change the whole motherboard.

Not very original, but hope to be of any help :)

---

### Post by QIII on 2012-04-16
If that was buzz as in electric component frying buzz and not system speaker, chances are good that that your nose or eyes can find the culprit.  A buzz loud enough to hear means a lot of current and an arc.  If it was an arc, hope like heck that it was in your PSU behind a fuse.  Otherwise, it could be ugly.

Unplug, open your case, lay it on it's side, use a ground strap and pull out everything that is not soldered down, including the PSU.  Check all of it for obvious scorched areas, melted solder, telltale smoke residue.  Check the mobo very carefull front and back.  Burst capacitors are easy to spot and mean a funeral is in order.  Use your nose, too.

If you don't find anything, put just the PSU and the board back in and power up.  If you get nothing, no beeps, no power lights, etc, either your mobo or your PSU are shot.  If you are not absolutely sure your PSU is fine, don't rush out and buy a new mobo - you might fry it, too. Try to power up and listen for post beeps.  Have your mobo documentation handy to interpret the beeps.  Then start putting the pieces back in one at a time until you either hit a post beep that stays the same after installing it or your machine powers up and runs.

---

### Post by coldraven on 2012-04-17
If you can see "Press delete for setup" then your most likely it is your hard disk that has failed.
Try this:
Boot up and press whatever button it suggests for "Setup"
This should take you to setup, otherwise known as BIOS.
In the BIOS screen go to the section "Boot"
Change the boot order so that the CD is first. There should be help tips on the screen to show you how to do it.
Then select "Save and exit"
Then try booting with a live CD and see what happens. If it boots but you cannot see your HDD in Nautilus then it is kaput.

---

### Post by mastablasta on 2012-04-17
if motherboard beeps only once then it is working ok.

---

### Post by Mark Phelps on 2012-04-17
Here's a link to understanding what the beep codes mean:

[http://www.pchell.com/hardware/beepcodes.shtml]("http://www.pchell.com/hardware/beepcodes.shtml")

However, these are BIOS vendor specific, so if your BIOS is not one of these, you will need to Google to see if you can find the list of beep codes they use.

Your motherboard is not DEAD.  If it was, you wouldn't get any video at all, just a black screen with no flashing cursor or anything.

---

### Post by davidvandoren on 2012-04-17
Chances are, that your motherboard's battery is empty and there for each time you unplug it from the main grid your BIOS changes it's date to 2003 or whatever. 

First try to get into the BIOS and make sure the date is set to current.

---

### Post by deserthowler on 2012-04-17
> **davidvandoren said:**
> Chances are, that your motherboard's battery is empty and there for each time you unplug it from the main grid your BIOS changes it's date to 2003 or whatever. 

First try to get into the BIOS and make sure the date is set to current.

Yes, your motherboard is not totally dead if you get any screen messages.

Look for visible damage on the board.  If there is none, check the BIOS to see if settings have changed.  That is about about the age when CMOS batteries start to fail but if it has been plugged in for a long time that shouldn't be a problem.

Earl

---

### Post by HiImTye on 2012-04-17
if you are receiving messages on your screen at boot time then your motherboard is not dead. hit delete or whatever button it asks you to press to enter the CMOS (or equivalent) and change the boot order to CD-ROM first. load a live CD and then use the partition editor (you will likely need to use 'edit menus' or 'menu editor' to gain access to it, depending on whatever version of the liveCD you have handy) if you see logical volumes, then use the file browser to attempt to navigate to it and see if you can read data from it.

---

