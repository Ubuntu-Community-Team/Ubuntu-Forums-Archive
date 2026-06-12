---
title: "Dual Displays"
date: 2006-04-19
forum: General Help
---

### Post by evillawngnome on 2006-04-19
IS there a good how-to somewhere? My preliminary google search wasnt very fruitful.

I have one monitor connected to the on board video of my mobo, and i have a second PCI graphics card i would like to use for a second display.

---

### Post by gondilon on 2006-04-19
if you go to this url: [http://www.tldp.org/HOWTO/Xinerama-HOWTO/](http://www.tldp.org/HOWTO/Xinerama-HOWTO/), it will tell you how to make multiple moniters and graphics cards into a continous display.

---

### Post by evillawngnome on 2006-04-19
Word.

---

### Post by luckyaba on 2006-04-19
What exactly are you trying to do? Stretch the screen between the 2 monitors, have each display showing the same thing?

---

### Post by evillawngnome on 2006-04-19
When i boot into windows, it lets me use the other monitor as additional desktop space. A linux translation would be if i could boot into the desktop, open up a terminal window and drag it from my primary display to the second display.

---

### Post by newpants2003 on 2006-04-19
[QUOTE=evillawngnome]When i boot into windows, it lets me use the other monitor as additional desktop space. A linux translation would be if i could boot into the desktop, open up a terminal window and drag it from my primary display to the second display.[/QUOTE]

Yes, i want know that too!

---

### Post by djsroknrol on 2006-04-19
might this link help?...

[try this]("http://ubuntuforums.org/showthread.php?t=162363")

---

### Post by luckyaba on 2006-04-20
i basically just added another copy of the monitor and device section in xorg.conf. Screen1 and screen2, screed1 i directed to PCI(the first grphics card) and screen2 to PCI(second graphics card). That is what your goal is right.. 1 monitor to the graphics card and 1 to the onboard one? If so i can post a copy of my xorg.conf file when i get home.

---

### Post by gondilon on 2006-04-21
how do I find the bus id of a dual headed graphics.

---

### Post by Zorro on 2006-04-21
[QUOTE=gondilon]how do I find the bus id of a dual headed graphics.[/QUOTE]


What graphics card you attempting this on? I know nvidia are great with dual heads (i use one on a dual setup)...


My xorg.conf looks like this...

Section "Device"
        Identifier      "NVIDIA"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"

       Option          "TwinView" "on"
       Option          "MetaModes" "1024x768,1024x768"
       Option          "SecondMonitorHorizSync" "28-80"
       Option          "SecondMonitorVertRefresh" "43-60"
       Option          "TwinViewOrientation" "RightOf"


EndSection


I hope that helps somewhat.. :-k

---

### Post by JoeMetal on 2006-04-21
Zorro, would you be able to put up the rest of your xorg.conf stuff?  I've been having trouble with mine since upgrading to Dapper and I'd like to fix it.

---

### Post by Zorro on 2006-04-21
No probs.. I assume you meant just the stuff relating to the dual screen ... If you want it all just let me know...


Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA"
        Monitor         "Generic"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by JoeMetal on 2006-04-21
So you don't need to do that Screen 1, Screen 2 thing at all?

---

### Post by Zorro on 2006-04-21
Nope, I read the *Option "TwinView" "on" *setting does it all...  So I didnt put it in ;) and it works like a charm...

---

### Post by luckyaba on 2006-04-21
The only reason i had to do screen 1 and screen2 is because im using 2 graphic cards. Not both monitors to 1 graphics card. Sorry i thought that is what he was attempting to do.

---

