---
title: "Unknown Screen - Cant change res. HELP!"
date: 2010-03-29
forum: General Help
---

### Post by gavlar on 2010-03-29
I've just installed a fresh install of 9.10 on this old PC.

However, when I go to change the resolution settings I get "Unknown" in red and it doesnt allow me to chose a res higher than 800x600.

I've read in other threads that I need to change the xorg.conf but I didnt really understand (Im a bit of a linux noob)

As I understand fresh 9.10 installs dont come with an xorg.conf; so I made one then entered this:```

Section "Device"
       Identifier "Configured Video Device"
       Option "RenderAccel" "true"
EndSection

Section "Monitor"
         Identifier "Configured Monitor"
         HorizSync 47.82
         VertRefresh 59.92
         Option "UseEdidFreqs" "1"
         Option "ReducedBlanking"
Modeline "1024x768@60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsynmode +vsync
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
        DefaultDepth 24
        Subsection "Display"
             Depth 24
             Modes "1280x1024" "1024x768" "800x600" "640x480"
        EndSubsection
EndSection
```

I got the modeline and refresh/sync rates from a cvt command in a terminal.

However, I still cant select 1024x768 from the Display settings.


PS. I dont know if the graphics drivers were installed by defult or not. Either way, when i go into the Hardware Drivers it finds no available drivers. This PC has a "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter" card.


Thanks for your help,
Gavin

---

### Post by gavlar on 2010-03-29
bump

---

### Post by gordintoronto on 2010-03-29
Look for "nomodeset," which you need to put into Grub.

---

### Post by gavlar on 2010-03-31
I've looked and cant find anything much about nomodeset...

How can I force Ubuntu to recognise this monitor?

---

### Post by gavlar on 2010-04-04
Bump

---

