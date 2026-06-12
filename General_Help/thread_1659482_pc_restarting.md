---
title: "pc restarting"
date: 2011-01-04
forum: General Help
---

### Post by skarosg3 on 2011-01-04
Hi all,
I have a problem the last few days, that neither me or anyone i have talked to know what the problem is.

I have a desktop with ubuntu 10.04, few days ago the machine started to restart it self at random intervals. there was times that i worked on it for hours with no problem, and then it just rebooted, and there was times that it barely made it to ubuntu before restarting. I think there was a time that restarted while still in bios.

i went to a service shop and told me that it was the psu, so we changed it, and it worked for 3 days nicely, but then it started all over again.

I have a secondary ntfs drive which i was told that it might have some virus, so i unplaged it and run the pc with out it. but 3 hours later it rebooted.

my question now is this( quite long intro isnt it?)
is it possible to be some kind of bug from the updates? if i update to the 10.10 version could it fix it if thats the case?
i guess i would be sure about that if i just reformated and install the 10.10, but i would like not to.

any help would be really appriciated.

thanks, ilias

---

### Post by fabricator4 on 2011-01-04
Unfortunately I think this is a hardware fault on the Motherboard.  There are a few things you an check before replacing the Motherboard, but in my experience the sooner you replace it the better off you'll be.  If it really did reboot during Post (ie showing the BIOS screen) then it's not a software issue.

1. Remove the memory and make sure the slot contacts and the pads are all clean.  Re-insert firmly and carefully.

2. Disconnect the reset button if you have one. Strangely enough I've had  a few problems like this that were caused by a faulty switch or badly fitting facia panel.

3. Remove all slotted cards that you can do without.  This eliminates any conflict problems or faulty hardware issues.  Given you've probably got onboard video and drive controllers, you probably don't really need any cards in there for testing purposes.

4. Make sure there's no loose socketed chips.  These days everything is usually soldered to the motherboard, which improves reliability, but make sure that if the chipset is socketed that they are tight in their sockets.  If it was me I'd remove the chips and re-insert them, same as for the memory. 

5. Make sure there's nothing shorting out on the mainboard, and make sure there's plenty of clearance between the back of the board and the metal case for the same reason.

6.  Find another PC Shop.  I would have checked all of these things before I replace the CPU. They didn't charge you for it did they?  ...


Chris.

Edit:

Oh, you said PSU, not CPU.  My bad.

Fair enough, it can't hurt but it's not the place I would have started.  PSU problems normally show up as failure to boot, not re-booting.  It's also one of the easiest things to test.

At this point I'll add test procedure no 7:

7.  Do a tap test on the motherboard.  That is, boot the machine and get something light and non-conducting like a plastic pen barrel and tap all all the chips/CPU and the board all around the CPU.  If you find a tapping place that seems to always result in a re-boot then it most likely indicates a broken track or a dry joint that is causing your problem.  You'll notice that the heatsink on the CPU is held in place by some springs or clips with so much force that it deforms the board.  Handled roughly at installation this is the sort of thing that can result in damage leading to the kind of problem you're having.

Regards,

Chris.

---

### Post by skarosg3 on 2011-01-04
wow! that was one detailed answer! :)

I thought that it is not a OS problem my self, but i wanted to make sure just in case there is anyu known issues with my version, or something that would save me some time and efford.

I will test your ideas and will let you know

---

### Post by skarosg3 on 2011-01-10
as strange as it might seems, i think you were right.
I unplugged the reboot cable and works two days now with no restart at all!

thanks for that, i would never think of that my self.

---

### Post by fabricator4 on 2011-01-15
> **skarosg3 said:**
> as strange as it might seems, i think you were right.
I unplugged the reboot cable and works two days now with no restart at all!

thanks for that, i would never think of that my self.

You're welcome.  I gave a fairly comprehensive (but low tech) trouble shooting guide for your problem.  Unfortunately most people don't seem to be able to follow a guide to the letter so end up missing the obvious - so kudos to you for finding the problem was the reset button.  

The obvious is usually only obvious after the fact.

It could still be that the problem is a dry joint or a broken track on the MB - sometimes disturbing the board can cause a problem to come or go, so you are very lucky if it real was such a simple fix.

Chris

---

