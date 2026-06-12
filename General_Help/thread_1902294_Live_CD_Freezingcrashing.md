---
title: "Live CD Freezing/crashing"
date: 2011-12-30
forum: General Help
---

### Post by Mrs Twaddle on 2011-12-30
To cut a long story short I'm trying to rescue data from a windows 7 laptop, with unknown BSOD's (been trying to solve it for over a week)
All hardware scans say system is fine, so we're working on the assumption that it is a corrupted system file.

Anyway, i burnt a copy of 11.10 and loaded up the live CD. (previously installed to another machine with this copy so i know it is fine)
Set up the network and opened folders for copy and paste.
Now it seems to be that the data being copied is fine (i'm copying to my linux machine)
BUT every now and then the laptop, with the Live CD, is freezing completely, or shutting down the explorer (unity i believe it is now)

Could this be indicating that there is indeed something up withe the hardware in the laptop, or is it a case of the Live CD only allocating so much memory space, and it's crashing with the amount of data being transfered?

---

### Post by 2F4U on 2011-12-30
While you say all hardware scans are fine, did you make and extended memtest, for example from the liveCD? If crashes happen unexpected and without obvious pattern, it always a good idea to look at the RAM. If the RAM is somehow defect, it may very well happen that you recognize it only after some time of work.

---

### Post by Mrs Twaddle on 2011-12-30
I have run numerous diagnostic scans, including a full scan with the Dell diagnostic disc, windows memory scan and memtest scans 
all showed no errors.
Most of our BSODs are happing at boot, tho some are happening when the laptop is being used.
Bsods are usually stating different errors, and we've tried upgrading/downgrading numerous drivers.
I've also opened her up and cleaned her out. tried each ram stick individually, but it is the only laptop we have so have no other parts to swap around to test.
But it's still occuring.

No point in formating her if the drive is on it's way out, but don't want to waste money if there is nothing wrong with the parts either.

---

### Post by Mrs Twaddle on 2011-12-30
Just ran another memory test, with our del diagnostic disc, all ok.
Running a more indepth hard drive test now.

Also managed to borrow a ram stick from a neighbour so i'll try that later too.

Does the Live CD crash if it is under pressure tho?

---

### Post by Mrs Twaddle on 2011-12-31
new ram stick had same crashing issues. Hard drive scan was fine, but given the live cd froze in the same way as the laptop does, browser shuts down on it's own too. There has to be a hardware fault. Can i scan the harddrive properly with the live cd. I checked it with gparted but it was only an 8 second scan.

---

### Post by Mrs Twaddle on 2011-12-31
i'm running a gsmart control scan. It says the harddrive is fine. The live cd logged me out when i was looking at the results though, and is now completely frozen. It's going to be "laptop,  meet bin", i think.

---

### Post by coldraven on 2011-12-31
I once had a laptop with a heat related fault. From cold it would run for 20 mins. then freeze.
Then after a few minutes it would run for 10 mins, then 5 mins etc
I had it totally in pieces but never found the problem.
If you time your machine between freeze ups you may find the same thing.
Try removing the hard drive, boot with the live CD and see if it still works after an hour or so.

---

### Post by Mrs Twaddle on 2011-12-31
it often blue screens from cold. As in first boot of the day, most of the freezes are happening to the browsers, web and file. I'll try the disc without hard drive to see if the disc runs better. It will also prove that it isn't the harddrive too.. Is there a way to test cpu, or motherboard. Because i'm at a loss.

---

### Post by Mrs Twaddle on 2011-12-31
40 mins in with live cd and no hard drive. System completely frozen. Started with repeatedly shutting down firefox, then compiz crashed. Posting this on my phone. Running gkrell and all was looking good. So it's heat related? Though thats not why we get blue screens?

---

### Post by 2F4U on 2011-12-31
It may be easy to verify whether it is heat related or not by putting it out in the cold and see if it runs longer. If it is not cold where you live, you can also put it in the fridge.

---

### Post by Mrs Twaddle on 2012-01-01
i don't think this is temp related. It's taken a few attempts to boot the live cd today. I installed gkrell and psensor to keep an eye, while testing your temp theory. And it's frozen at max of 10 mins, gkrell is showing low cpu usage and psensor is showing a max temp of 52, current is 48. Laptop completely frozen, will have to force shut down. Fan is spinning ok. Air doesn't feel hot coming out. Going to try leaving it for 5 to see if it unfreezes.

---

### Post by Mrs Twaddle on 2012-01-01
actually considering the laptop is frozen i think it is blowing hotter than it should be from the fan vent, other areas feel cooler.

---

### Post by syerges on 2012-01-01
Many similar problems have been the result of heat and cheap cd/dvd drives from my past experiences. Can you run with you CD-Rom off? If so, give it a try, could be a simple easy replacement. Otherwise you are looking at trouble.

---

### Post by Mrs Twaddle on 2012-01-01
i'll try that. Will have to burn ubuntu to usb first.  I do get freezes on windows 7 with no cd/dvd in. I'm testing with wlan disabled now.

---

### Post by Mrs Twaddle on 2012-01-01
if i'm honest i think we have a major problem. I'm still getting bsods on windows. We've rescued/backed up most data, so if it's a format then fair enough. But due to the problems with ubuntu live cd, i know we have other issues. Current possible culprits, graphics chip. Wlan chip, heat, cpu or maybe even motherboard. I'm fairly confident ram and harddrive are ok. Worst thing is laptop has just gone past warranty. Froze again! Time for shopping i think.

---

### Post by Mrs Twaddle on 2012-01-04
i figured out the problem. There is a setting in my bios for my cpu, i think it was called intel sidestep, or smartstep. Since i disabled it the laptop has been fine in both windows and linux. Could it be a sign of my cpu failing? I've tried updating the bios but it makes no difference, and it can't be drivers as it affects both windows and linux.

---

