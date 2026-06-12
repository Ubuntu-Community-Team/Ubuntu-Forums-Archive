---
title: "Multi-Monitor Support Improvements"
date: 2010-09-29
forum: General Help
---

### Post by cfree220 on 2010-09-29
Hi guys (or should I say, wizards?),

It's been a little while since I've had to look under the hood of my '09 model Ubuntu. I've recently gotten into the habit of using a dual monitor configuration so that I can write papers with a word processor on one screen and a browser on the other.

I feel like I was able to get this system fairly streamlined in the past, but I cannot recall how I went about it. It's somewhat inconvenient to have to configure my monitors every time I want to use them, as this requires that I launch the nvidia control panel, enable the external monitor, change the relative positioning, and then wait for the changes to take place.

Some bug also adds in an extra step. It doesn't matter which monitor I check off as being the primary display-- my panels and/or docks always end up on the secondary monitor the first time the changes are applied. I can get them on the desired monitor by making a minute change to positioning of the screen and by then re-applying the settings. While it is a workaround that works 100% of the time, it becomes really inconvenient for someone who shuts down their machine whenever they are not actively using it.

When I try to save my configuration to the X configuration file, I get the following error:

```
Failed to parse existing X config file '/etc/X11/xorg.conf'!
```

If anyone could shed some light on the problem, it would be greatly appreciated.

Also, if anyone knows of other ways of managing multiple monitors/if newer versions of Ubuntu do the job better than Karmic, that would also be helpful.

Other info:

Computer: Dell XPS M1530 (laptop) with
Primary Screen: Seiko 1920 x 1200
Secondary Screen: emachines EMA E19T6W 1440x900 (over VGA)
GPU: NVIDIA GeForce 8600M GT (512 mb dedicated)
OS: Ubuntu 9.10 and Windows 7 Professional (x64) (Don't worry, I NEVER use Windows).


Thanks in advance!

--Chris

---

### Post by tiznom on 2010-09-29
I remember running into this problem, too. First, back up your existing xorg.conf file by copying and pasting it to the desktop. It's at etc/X11/xorg.conf.

In the NVIDIA settings window, once you click "Save to X configuration file", click on "Show preview..." to get the text output you need. This is your new, corrected display settings. Leave this window open for a minute while you do the next step.

You need to be root to overwrite the current xorg.conf, so type "sudo nautilus" in a terminal window, opening your file browser as root. Browse to etc/X11/xorg.conf and open it, choosing Display to display its contents. Highlight it all, delete all the text (You did back it up in step 1, right?) and copy and paste all the text from the Save X Configuration/Show preview window you left open in the last step. Save, close, and close the root terminal window. Cancel out of the NVIDIA windows, and reboot. You should be good to go at this point. 

Someone will probably post an even easier solution here but this absolutely worked for me and I do it this same way every time.

---

