---
title: "(EE) Problem/Error Passing Config [ATI Graphics]"
date: 2009-08-14
forum: General Help
---

### Post by mit10 on 2009-08-14
So I have been trying to get my ATI video card to work for 6 hours without asking for help. Annndd... as you can see I have failed! :) haha! So I am coming to all you wonderful people! Please keep in mind I am new, so lamans terms please, or you will get a blank stare and another :confused:

First things first. 
Graphics Card: Radeon x1200 series
I have completly purged my system of all fglrx files
When I boot my computer all goes well until my graphics card is being read (or so what I assume) I get these two errors

(EE) Problem Passing config file
(EE) Error Passing config file 

(I thought Error and Problem were the same thing! HAha! I found this funny :P)

My drivers are available and are rendering but my computer has to go into a low graphic card setting for me to log on. So as you can guess my graphics are very slow right now. But at least I am able to use the computer.

I have been using this ["Open source" installation guide]("https://help.ubuntu.com/community/RadeonDriver")

I get everything working great up until I start messing with /etc/X11/xorg.conf
This is what I changed in the file

Section "Device"
    Identifier      "Radeon x1200"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
    Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       
        VertRefresh     
EndSection

Section "Screen"
    Identifier      "Default Screen"
        Device          "Radeon x1200"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

I also get this blue screen saying:
" There already seems to be an X server on display :0. Should another display be tried? Answering no will cause GDM to attempt starting the server on :0 again" 
<Yes>       <No>

If I pick option "yes" then it boots into ubuntu in low graphics mode.

If I pick option "No" then it sends me right back to the blue screen. The message also says something about pressing ctrl+alt+F7 to go to a different console I tried it and it gives me a black screen with a user name promt (example: poop@poop-computer: _ ) Obveously, I dont know how what to do there. 

So I hope this is enough information. But for now... I hope you guys will take the time to help me out. Thank you gentlemen (and ladies)!

---

### Post by dcstar on 2009-08-14
> **mit10 said:**
> 
..........
I have been using this ["Open source" installation guide]("https://help.ubuntu.com/community/RadeonDriver")

I get everything working great up until I start messing with /etc/X11/xorg.conf
This is what I changed in the file

Section "Device"
    Identifier      "Radeon x1200"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection
.......

You do not just copy configuration from someone else's system into yours without modifying it to match your hardware.. You do not need to change anything in your xorg.conf file (as it says clearly in those instructions).

You need to restore your xorg.conf file to what was there originally, that is now the root source of your problems.

---

