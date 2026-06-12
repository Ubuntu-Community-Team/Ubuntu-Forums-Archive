---
title: "How to Manually Set Xorg if your Monitor isnt Supported"
date: 2010-07-26
forum: General Help
---

### Post by rugbert on 2010-07-26
My ViewSonic VX2000 was being identified by my GPU so I couldn't get very good resolutions, like I couldn't even break 1024x724 which simply was not cool. Here's what I did to fix it, it might help some of you! Sorry if this is a repost :/

_**1) Google the manual for your monitor and get the specs.**_
**Prevalent information: **
[INDENT]_horizontal sync RANGE_ (may say f [sub]h[/sub] )[/INDENT]
[INDENT]_vertical refresh RANGE_ (may say f[sub]v[/sub] )[/INDENT]
[INDENT]_Supported screen resolutions_ ( and what refresh rate each resolution uses.[/INDENT]

**example**: My ViewSonic VX2000
[LIST]
[*]horizontal sync: 30 - 82kHz
[*]vertical refresh: 50 - 85 Hz
[*]supported resolutions (ones I care about anyway): 
[LIST]
[*]1600 x 1200 @ 60 Hz
[*]1280 x 1024 @ 60, 75
[*]1024 x 768 @ 60, 70, 72, 75, 85 Hz
[/LIST]
[/LIST]
[U][B]2) Open up xorg.conf (as root) and find the Monitor section - Its labeled as Section "Monitor"
[/B][/U]     
 Add or edit these lines with the ranges you found:
[INDENT][I]           HorizSync
           VerRefresh
[/I] [/INDENT]     Note - The ranges should be in the format of *xx.x - yy.y* **[COLOR="Red"]!!pay careful mind to spaces!![/COLOR]**

**example**:     [I]HorizSync       30.0 - 82.0
                  VertRefresh     50.0 - 85.0[/I]
**_3) In terminal, enter the following command to xorg configurations for your resolutions based on refresh rates:_**
*gtf vertical-resolution horizontal-resolution refresh-rate*

**example:**    
[INDENT] [I] gtf 1600 1200 60
              gtf 1280 1024 60
              gtf 1280 1024 60
              gtf 1024 768 60[/I][/INDENT]

Each of these commands will pump out some information you need to copy pasta into xorg.conf at the end of the Monitor secion.
**example**:
 [INDENT] [I]# 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
  Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync[/I][/INDENT]

**4) Now move down to the Screen section**. Anything that says "depth" in it is your color depth, like 24 bit, 32bit ect. change that to whatever is appropriate.

In the Screen Section, there should be a sub section called, *SubSection*
          
Add of edit the modes line to have your resolution options in the following format (each option is in quotes)
[INDENT]
          * "VERTICALxHORIZONAL@REFRESH"*
[/INDENT]**example**:
[INDENT]* 	Modes	"1600x1200@60" "1280x1024@75" "1280x1024@60" "1024x768@60" "1024x768@70"*[/INDENT]

**5) Thats it!** Sure you can go can change the Identifiers for the monitor, screen, devices, and server sections but as I found out, it doesnt really change anything other than make it easier to ID. And unless you have multiple monitors theres no point. **Also - if the Identifiers dont match then it will kill X when you reboot**

**6) RESTART -** I had a few problems when I restarted, but only because of typos. For instance, my VertRefresh was set at *50. 0 - 85.0* That space between *50.* and *0 *killed it for me.

Let me know if anything should be added!

---

