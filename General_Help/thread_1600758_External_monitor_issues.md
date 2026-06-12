---
title: "External monitor issues"
date: 2010-10-19
forum: General Help
---

### Post by slonnnik on 2010-10-19
Hi

Please help me with following issue. 
I have connected external monitor to my Laptop. Everything works fine except the monitor goes blank sometimes. ( if I do nothing it turns of saying: "NO signal") If I move the mouse the monitor turns on again. And this repeats several times.

My video card: Ati Mobility Radeon X1600

My xorg.conf:

Section "Device"
        Identifier      "Radeon x1600"
        Driver          "ati"
    BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Belinea"
     
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon x1600"
        Monitor         "Belinea"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection



PLease help me set this up right.

Thank you

---

### Post by realzippy on 2010-10-19
Screensaver?Is it after 15 minutes?

---

### Post by slonnnik on 2010-10-19
no. it is not screen saver. it happens when I'm doing something....writing, moving mouse..
and it happens only sometimes...not regularly. mainly when I start the computer

---

