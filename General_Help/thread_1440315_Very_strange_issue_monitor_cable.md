---
title: "Very strange issue monitor cable"
date: 2010-03-27
forum: General Help
---

### Post by ade234uk on 2010-03-27
Ok, well I have got to say this is the most irritating issue I have come across. I currently have a benq monitor G2020HDA

The monitor cable that came with it, started to turn the screen yellow, so I purchased a new VGA cable. Fine I thought. Went to boot Ubuntu and the best resolution I could get was 800x600. So I thought that I might have bought a bad VGA cable, so I bought another one. Same issue again, Ubuntu no longer detects my monitor and the best resolution it can give me is 800x600

This is really frustrating. Why is it the cable that came with my monitor detected my Monitor in Ubuntu, and yet I have now used two different VGA cables, and Ubuntu cannot detect any monitor.

Does anyone have a solution for this? I never realised that there was a difference with VGA cables.

---

### Post by Strongman332 on 2010-03-27
Make sure it is not soft ware related, check your computer with a live cd. 

next up if your using a graphics card, uninstall it and try to use the integrated card (disable drivers first)

---

### Post by ade234uk on 2010-03-27
I have tried both live CD and also installed Ubuntu fully on two seperate machines and it still only gives me a resolution of 800x600.

All I can say about this, is that I have never ever seen this sort of issue before. The cable that came with the monitor worked fine and offered me the proper resolutions and also detected the monitor,

Either some thing is wrong with my monitor 
or 
The cables are not compatible with the monitor which I is a crazy ides
or
The cables are rubbish.

---

### Post by varunendra on 2010-03-27
With extremely limited knowledge about VGA signals, here's all I can suggest:
Check this out (hope this helps):-
([http://pinouts.ru/Video/VGA15_pinout.shtml](http://pinouts.ru/Video/VGA15_pinout.shtml))
Accordingly, check it with your manual for troubleshooting; ([download manual]("ftp://211.78.86.210/monitor/lcd/manuals/g2220hd/lcd_monitor_um_user_manual_20090213_142612g2020hd%28a%29-g2220hd%28a%29_en.pdf"))

Note that pin nos. 4, 11, 12, 15 are used for monitor ID bits, so check their connectivity (& compare with the original one).

If the screen turned plain yellow with original cable, then I guess any one or more of the colour signal pins were either grounded or disconnected (refer to manual pg no.29)

Personally, I don't think VGA cables can have difference in connectivity. Continuity check would be the best way to confirm this.;)

And you may be right saying *"Either some thing is wrong with my monito"  *if changing cables or machines isn't working!
Check the original cable with some other monitor if you can.

---

### Post by ade234uk on 2010-03-27
Thank you very much for this info

---

### Post by ade234uk on 2010-03-27
I'm going to pick my monitor up from the office and see if I get the same issues. If not then my monitor is the problem. If it does the same then it means I have two rubbish VGA cables. I would call myself a reasonably experienced user, I can build PC's, I can build websites, but I cannot believe something so minor is giving me this hassle.

---

### Post by Mark Phelps on 2010-03-27
> **ade234uk said:**
> The monitor cable that came with it, started to turn the screen yellow, so I purchased a new VGA cable. Fine I thought. Went to boot Ubuntu and the best resolution I could get was 800x600.

The fact that you have had three monitor-hardware related failures in a row, despite changing cables, makes me guess that the monitor has gone out.

While it's POSSIBLE that both of the new VGA cables are bad, it's very unlikely.

Did that color change when the monitor had been in use for a while and was hot?  IF so, that's the same thing that happened to an old Dell flat panel of mine, except in my case, it turned Red.

---

### Post by realzippy on 2010-03-27
[http://ubuntuforums.org/showpost.php?p=9036619&postcount=5](http://ubuntuforums.org/showpost.php?p=9036619&postcount=5)

---

### Post by varunendra on 2010-03-27
> **ade234uk said:**
> Thank you very much for this info
Pleasure!

> **Mark Phelps said:**
> Did that color change when the monitor had been in use for a while and was hot?  IF so, that's the same thing that happened to an old Dell flat panel of mine, except in my case, it turned Red.
Lose contacts or grounding of signal pins due to heat (at picture-tube's neck) used to be a problem with CRT monitors especially when they got old; but I haven't come across any TFT or LCD that dissipates so much heat. Sounds strange for a TFT/LCD but can't disagree since you've experienced it.
Whatever... I believe it may be some connectivity issue from inside the monitor... that's why I suggested to check the original cable with the same machine, but a different monitor

> **realzippy said:**
> [http://ubuntuforums.org/showpost.php?p=9036619&postcount=5](http://ubuntuforums.org/showpost.php?p=9036619&postcount=5)
Useful Info..... 
But if your monitor is within warranty period, better not mess with it - rather get it replaced (obviously after making sure it IS faulty !!);)

---

### Post by djg10 on 2010-07-07
I have the same issue..i returned the new vga cable back & now i m tryin to use the original cable...i have dual boot to win xp..& the monitor and new cable r fine...the resolution is not affected in xp...its some issue with ubuntu..i have not yet found any solution to this... :(

---

