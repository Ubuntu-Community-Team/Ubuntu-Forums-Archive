---
title: "fglrx reverting to low resolution."
date: 2010-06-07
forum: General Help
---

### Post by hangfire on 2010-06-07
I recently reinstalled using the latest "respin" CD ISO. Before that, I had other problems with 10.04, but X and fglrx worked perfectly.

Now, X always comes up in 1600x1200 instead of the monitor native 1920x1200. I am still using the same on-board Radeon 4200. Supposedly this display adapter is very well supported by Linux???

I did an **aticonfig --initial** as suggested in the [Known Lucid Lynx issues/bugs]("http://ubuntuforums.org/showthread.php?t=1469475") with workarounds thread, but when I restarted X I got a black screen, and when I rebooted, even though xorg.conf now says 
```
Option      "PreferredMode" "1920x1200"
```
The system still comes up in 1600x1200. Note it is on DVI and I never touched the hardware or put a bad cable on it since it was working with the first install of 10.04.

When I go into Catalyst Control Center, Display Manager, Display Properties tab, the highest resolution available is 1600x1200. I hand-edited X11 and restarted and ran for a while in 1920x1200, but that no longer works. Now I just get a black screen whenever I restart X, and it always starts in 1600x1200.

How do I convince fglrx that I really have a 1920x1200 monitor? (VP2330wb). It is really very blurry in 1600x1200.

-HF

EDIT: Ran get-edid, got:
```
get-edid: get-edid version 2.0.0

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0xc01cc "ATI ATOMBIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
```

Do I have bad H/W?

---

### Post by hangfire on 2010-06-08
Bump.

---

### Post by hangfire on 2010-06-08
Bump.

---

### Post by hangfire on 2010-06-08
Bump.

---

### Post by hangfire on 2010-07-04
RMA'd the Gigabyte (this issue), bought a new Asus M/B with an HD4290, same problem. Can't read edid with get-edid. Same issue in open source, Ubuntu packaged fglrx, and latest fglrx from amd.com.

Without talking to the monitor, the system doesn't offer the highest resolution as an option. I'm pretty sure that I can fix this with a custom, hand-written xorg.conf (hmm takes me back to the 90's, only it had a different name back then), and I'm searching for it, but there are SO MANY people having problems with AMD cards that it is hard to find the info I need.

BTW The silence on this forum is deafening.

-HF

---

### Post by QIII on 2010-07-04
> **hangfire said:**
> Supposedly this display adapter is very well  supported by Linux???

Common misconception.  OEM hardware is not supported by OSs.  OEMs  create drivers to work with various OSs.  Adding to the complexity, mobo OEM Xmobos takes a component from YVideoAdapters and slaps them together.

Thus, the problem is not "Linux doesn't support my adapter."

Did you consider that the deafening silence is due to the fact that nobody has a solution to your specific problem or simply did not see your post when he or she was awake and brewing tea in Bangalore?  As I am sure you are aware, we are all volunteers here, we live all around the world, we do not have access to all the specifications and source code for every possible piece of hardware and its driver and do not have a garage full of various hardware components to switch out and troubleshoot.

Although this is not exactly your problem, it might be informative.
[http://ubuntuforums.org/showthread.php?t=1464748](http://ubuntuforums.org/showthread.php?t=1464748)

Should things be this difficult?  No.  Does anyone in the Linux community control how every piece of an integrated board works with every possible combination you can buy on the street?  No.

If it doesn't fit the bill, send the guy a note and see if he can add anything to this thread.  He seems fairly knowledgeable.

---

### Post by hangfire on 2010-07-04
> **QIII said:**
> Common misconception.

I know very well that AMD is the problem here. However with sites like Phoronix crowing about every little update AMD makes to proprietary drivers, Canonical integrating pre-release fglrx hot from AMD, and every spec released into the open on older adapters, plus glowing reports from users, there seemed to be support. If I had a 1600x1200 monitor instead of a 1920x1200, I wouldn't even know there was an issue with EDID reading and mode settings.

> **QIII said:**
> 
Did you consider that the deafening silence is due to the fact that nobody has a solution to your specific problem or simply did not see your post when he or she was awake and brewing tea in Bangalore?


I started this thread 3 WEEKS ago. I didn't expect 1 hour response.

> **QIII said:**
> 
Although this is not exactly your problem, it might be informative.
[http://ubuntuforums.org/showthread.php?t=1464748](http://ubuntuforums.org/showthread.php?t=1464748)


Thanks, I'll check it out.
> **QIII said:**
> 
Should things be this difficult?  No.  Does anyone in the Linux community control how every piece of an integrated board works with every possible combination you can buy on the street?  No.


If no one reports to the forum, opens launchpad reports (I've opened several on other issues), etc., then no one at AMD or Canonical will know or care that there is a problem. Right now the proprietary driver support is in disarray, with many perfectly good adapters being brushed aside due to kernel mode setting support by Xorg, and it is giving Linux a black eye (even though it is Xorg's fault, not kernel.org or Canonical).

I bought this system based on the idea that it was well supported. I feel it my duty to provide some search engine fodder otherwise.

-HF

---

### Post by QIII on 2010-07-04
This forum is intended for community support.  It is not a place to report bugs.  The developers may not even come here.

Launchpad, as you have mentioned, is the place to report bugs -- with Ubuntu.

This is an OEM support issue, and it probably needs to be reported "upstream" to the OEM.

---

### Post by hangfire on 2010-07-05
> **QIII said:**
> This forum is intended for community support.  It is not a place to report bugs.  The developers may not even come here.

Launchpad, as you have mentioned, is the place to report bugs -- with Ubuntu.


I agree. Besides looking for help, I am trying to reach potential buyers to warn them about these issues.

> **QIII said:**
> 
This is an OEM support issue, and it probably needs to be reported "upstream" to the OEM.

I have made progress. The DVI port reports EDID information, and is now running the monitor at 1920x1200. This does not mean I have a bad monitor VGA side, it means there is a problem with the HD 4290 (and the HD 4200 I RMA'd as well) on the VGA port, as Windows 7 now is happily downloading EDID information on the VGA port, knows what monitor is attached and all its capabilities. (The two computers share the same monitor).

An OEM driver bug, certainly.

-HF

---

