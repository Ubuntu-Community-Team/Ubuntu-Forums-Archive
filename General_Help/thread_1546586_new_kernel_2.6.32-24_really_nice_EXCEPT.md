---
title: "new kernel 2.6.32-24 really nice EXCEPT"
date: 2010-08-05
forum: General Help
---

### Post by cloyd on 2010-08-05
This morning I checked for updates, and there was a new kernel out there, 2.6.32-24. Updated. I have been using a 2.6.34 kernel on my computer for a variety of reasons, most having to do with wireless connection and overheating The first lucid kernel regularly idled over 60 C. The 2.6.34 idled  in the 50's C. This new one 2.6.32.24 is staying in the high 40's unless I watch flash video's, then it gets to the 50's.  Not at all bad. Wireless works great with this. 

I've noticed two problems. The first was when I tried to suspend it this morning. I could not restart it. All I got was a blank screen. I ultimately had to force a shutdown with the power switch, and then when I restarted, the wireless was disabled, and it didn't want to restart (finally did, though).

Next, I decided to print. The print job was "processing" but nothing was happening. I rebooted into my old 2.6.34 kernel, and the print job rolled off the printer before I could open the file I wanted to print. 

Rebooted to the new kernel, and still couldn't print. So far, the print job has been processing for 24 minutes with nothing happening. This is a lexmark x2600 printer with lexmark's driver.  When I get home tonight, I'll try it on my hp photosmart plus.

Gateway LT3103u
HID compliant mouse
 Synaptics PS/2 Port touchPad
 Generic PnP Monitor
 Atheros AR5B95 Wireless Network Adapter  9285
 Reltek PCIe FE Family Controller
 AMD Athlon(tm) Processor L110
 Realtgek High Definition Audio
 Microsoft iSCISI Initator
 
 

 I've noticed in the forums that in general, this machine, has had a few problems handling lucid. 

I like the fact that this kernel runs cooler. I can do without suspend. But I really need to print.  I'll likely use the new kernel for just surfing and watching videos, but I need to print to use it all the time.  Has anyone else had a similar issue? Have they found a work around?

EDIT: Went to the house. The HP printer printed.  Things look better. Maybe I can work some more on the Lexmark. It is touchy. (don't think I want another one). Suspend is still an issue, but not as serious.

---

### Post by cloyd on 2010-08-06
bump.

Really, I have got to figure out how to get more people to answer my posts. However, I will figure this out, and I will post it as solved. (I've found, solve it, and people start chiming in). Hope I can help someone else.  I may not work on it much until week after next, as I'll be out of town most of next week. But I really don't know what the 2.6.34 kernel is supposed to be for . . . I think it is a new kernel that hasn't been fully tested by Ubuntu developers. It gives a few error messages while booting, but otherwise works well. But this new 2.6.32-24 kernel runs cooler, video does not crash, and wireless works well and I don't get those error messages while booting. That seems to tell me that if the tweaks I will have  to use to get it fine tuned on my little Gateway netbook may been much simpler than the ones I had to use on the 2.6.34 kernel.

---

### Post by clhsharky on 2010-08-07
cloyd

Try the kernel 2.6.35-14 patched by Ubuntu for Lucid.
It should give the PM and drivers your desiring,
[http://ubuntuforums.org/showpost.php?p=9684721&postcount=4](http://ubuntuforums.org/showpost.php?p=9684721&postcount=4)

Sharky

---

### Post by eigenman on 2010-08-07
Do you think at this point the wireless after suspending and printing are related?

---

### Post by cloyd on 2010-08-09
Returned to the office on Mon morning, and tried it out on the Lexmark. No go.

Really, I don't think wireless and suspend are related. Suspend doesn't work, and wireless works well w/2.6.32-24. This kernel is running about 5 C cooler than any other. Suspend and printing is the problem, and it prints with my HP, but not with my lexmark x2600. The lexmark prints on other kernels. I just tried the 32-24 after restarting cups, and it still did not work. But it is cooler.

The 2.6.35 runs about like 2.6.34, but wireless does not work well when signal is not very strong. 

When I have to print on the lexmark, for right now, I many have to use the other kernels. It may well be worth rebooting (in order to use the 32.24) with the temp drop, but wish I could fix this.


EDIT: Just tried suspending again, and it worked!  If this is consistent, my only problem may be the printer. (Once I get rid of this Lexmark, I can't ever imagine a good reason to buy another one!)

---

