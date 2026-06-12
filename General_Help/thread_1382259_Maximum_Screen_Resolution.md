---
title: "Maximum Screen Resolution"
date: 2010-01-15
forum: General Help
---

### Post by Dbtm on 2010-01-15
Hello. 

I just made a fresh installation of Ubuntu Karmic, but I can't set up my screen resolution correctly. My monitor resolution (1680 x 1050) is not listed in 'Display Preferences' or in my card's proprietary software (ATI Catalyst). The maximum resolution I can select is 1440 x 900.

xrandr detects a maximum resolution of 1440 x 1440 and displays the same list of screen resolutions as 'Display Preferences'. I tried to add a new mode following this guide: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")


But when I enter the line:

xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

I always get this message:

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  23
  Current serial number in output stream:  23

So I'm really desperate. It was sooo easy with displayconfig-gtk. What can I do to change my screen resolution? Any help would be deeply appreciated!

---

### Post by Dbtm on 2010-01-18
Anyone?? I also tried:

sudo dpkg-reconfigure -phigh xserver-xorg

But this command does nothing! What gives?

---

### Post by Dbtm on 2010-01-20
Still lost...

I tried modifying the xorg.conf file but failed again. First, I tried adding these lines under the Screen Section:

SubSection "Display"
		Virtual   1680 1050
EndSubSection

After that, I tried adding 'Section "Monitor"' and specified the modeline I obtained previously with cvt.

Making these changes had no effect at all in my system. Am I doing something wrong? What else is there for me to try????

---

