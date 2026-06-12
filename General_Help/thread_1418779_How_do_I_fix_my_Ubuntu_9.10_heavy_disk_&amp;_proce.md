---
title: "How do I fix my Ubuntu 9.10 heavy disk &amp; processor usage at idle?"
date: 2010-03-01
forum: General Help
---

### Post by FuturePerfect on 2010-03-01
[FONT="Arial"]At idle, I see my laptop's disk activity light flickers like a strobe and my system monitor show around 90% processor usage.

Although a newbie, I've managed to log IOTOP and TOP statistics, and I'm not 100% sure what they mean.  However, from my samples, it looks like neither IOTOP nor TOP show the saturation I see.

I have searched for various solutions, and tried all that seemed to apply, but none have fixed the above problems.  I have tried:
-removing gnome-system-monitor (since no change, I reinstalled)
-logging out (no change)
-workaround for a graphics problem that didn't fix these problems

The graphics problem workaround stops a continually spinning cursor and restores the titlebar/tabs and min max close buttons which are all missing from any windows opened when I first boot.

This workaround consists of selecting the Preferences | Appearance app, using the <- key (to get to the Visual Effects tab I can't see), then clicking on the Normal: radio button (the None: button is already selected, since Compiz won't use my graphics chip).

My old laptop searches for a driver that doesn't apply, the screen eventually blanks; I get the dialog that "Destop effects could not be enabled"; I click OK and my cursor and titlebar/tabs are fine!

If it helps, my graphics chip is a VIA/S3G Unichrome Pro IGP (using up to 64 MB shared memory) on an Averatec 3270 laptop; 1 MB RAM; dual boot Ubuntu EXT3 and XP NTFS plus NTFS data partition.

I don't want to reinstall 9.10 so I don't have to refind all my many settings for Shutter, Dockbarx, PDF MOD, Main Menu, etc.  I've spent 3 fruitless days on my own and hope you can help me.

9.10 has all patches; same apps/settings work fine on a test PC.

?is there maybe some startup program that got disabled?
?does my graphics workaround aid my processor/disk saturation?
?would removing Compiz (which parts?) maybe solve this?

I've been planning to use this on a trip in 3 days; hope I can.[FONT="Arial"][/FONT][/FONT]

---

### Post by dcstar on 2010-03-01
> **FuturePerfect said:**
> 
........
This workaround consists of selecting the Preferences | Appearance app, using the <- key (to get to the Visual Effects tab I can't see), then clicking on the Normal: radio button (the None: button is already selected, since Compiz won't use my graphics chip).

My old laptop searches for a driver that doesn't apply, the screen eventually blanks; I get the dialog that "Destop effects could not be enabled"; I click OK and my cursor and titlebar/tabs are fine!

If it helps, my graphics chip is a VIA/S3G Unichrome Pro IGP (using up to 64 MB shared memory) .........

You do not have a 3D driver for the Graphics chip - you should be using "None" for effects.

Trying to force anything else causes problems.

---

### Post by FuturePerfect on 2010-03-01
[FONT="Arial"]David:[/FONT]

Thanks.  Alas, I was not clear.  Visual Effect is always "None:", that is:

-it's "None:" before I try to fix the spinning cursor and all windows missing titlebar/tabs and min max close buttons;

-and it's still "None:" after I click OK to "Desktop Effects could not be enabled" (since Compiz doesn't work with my graphics chip, Visual Effects stay maked as "None:" after it tries and confirms that my chip won't allow "Normal:" effects)

-only somehow, the process of trying and not being allowed to get the system to set "Normal:" effects, stops my spinning cursor and restores my titlebar/tabs and min max close buttons.

---

### Post by Pjotr123 on 2010-03-01
This might help:
[http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m](http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m)

---

### Post by philinux on 2010-03-01
@Future perfect.

Can you post a screenshot of top.

And what does this command show.

```
free -m
```

---

### Post by FuturePerfect on 2010-03-01
Phil:

Thanks for requesting more information.

Since I'm still learning how to post, hope my attached screenshots in pdf format are OK--it was the most obvious way I could see to provide this info.  

Re My attached output from Top:  I've included only those detail lines that show non-0.0 in the %CPU column.

My attached output from free -m is straightforward.

Let me know if I can provide any additional information or testing.

---

### Post by FuturePerfect on 2010-03-01
Pjotr123:

Thanks for the your link to a great page with solutions to eight bugs in Ubuntu.  At idle my memory an swap are OK, but I'll be sure to check for these problems as I run more programs.

Since my laptop uses the Ralink RT2500 wireless chip, the solution for assuring proper throughtput with it should come in handy (when I solve my memory/disk saturation and can run my laptop more frequently without fear it will self destruct)

---

