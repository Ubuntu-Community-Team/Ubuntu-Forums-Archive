---
title: "Modeline for Vizio 32&quot; TV?"
date: 2010-09-10
forum: General Help
---

### Post by cisasteelersfan on 2010-09-10
I have an Nvidia GeForce 6150 integrated video card, and my TV is a Vizio VW32L. I installed the latest recommended driver from the Hardware Drivers. When I open the utility, I can select 1360x768, which is pretty close I thought. I selected this and hit apply, but it cuts off both the right and left side of the screen. For example, I can't see the Applications in the upper left corner. I went in to the TV menu and auto-adjusted, but it still cuts off both sides. I looked around the forums a bit and it sounds like I have to create a modeline. This is from my manual:

[LIST]
[*]1366x768
[*]60Hz  
[*]47.55 H.Freq (kHz) 
[*]59.81 V.Freq (Hz) 
[*]Positive H.Sync  
[*]Positive V.Sync  
[*]85.50 Pixel Freq (MHz)
[/LIST]
I typed this in on [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl") and got the modeline:
[LIST]
[*]Modeline "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807 
[/LIST]

Can anybody verify these settings? Or am I going to screw up my TV? Also, I'm pretty new at this. Where in the xorg.conf file do I put this information?

I was looking at other threads and I think I have to add +HSync +Vsync to the end, because my manual says they're both positive, right?

Any suggestions are greatly appreciated.

---

### Post by cisasteelersfan on 2010-09-10
I just found this in another thread:
> Something I posted in another thread, works best if you do all of this via ssh from another machine.
Find your TV's optimal resolution from the manual or online (eg 1366X768@60)
Issue the gtf command:
Code:
```
gtf 1366 768 60

  # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```
In your xorg.conf, under your monitor section add the gtf modeline output

Code:
```
Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Proview"
        ModelName      "Unknown"
        HorizSync       31.0 - 80.0
        VertRefresh     56.0 - 75.0
        Option         "DPMS"
        Option         "ExactModeTimingsDVI" "True"
        Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```
and under the screen section add the modeline reference (using only one "Modes" until you find a few that are appropriate, works best)

Code:
```
SubSection "Display"
                Depth       24
                Modes   "1368x768_60.00"
        EndSubSection
```
Next issue "/etc/init.d/gdm restart" and hope the overscan is fixed. If it is not a compatible resolution, the screen won't show anything (out of range or something). This is why using ssh is the best approach.

If that "gtf" does not work, you may need to try a different "gtf" depending on your tv resolution. My monitor (1366x768 had an optimal resolution using "gtf 1344 770 60" so don't be afraid to tweak the gtf until you get something that fixes the overscan.
Should I follow this advice? I don't know what SSH is so I won't be doing that... If the screen is out of range, what will I do to get back to Ubuntu? Thanks again.

---

### Post by cisasteelersfan on 2010-09-11
I got it. I followed that guy's advice, and I thought putting 1368 was a typo. When I had the modeline as 1366, it didn't work. I only worked with 1368. Now my monitor looks perfect!!

---

