---
title: "Problem with xorg.conf"
date: 2010-08-29
forum: General Help
---

### Post by cjmabry25 on 2010-08-29
So, I went back to 9.10 because I couldn't get my x1300 card to work right. Everything worked fine out of the box but then I read about the RadeonHD open source drivers and decided to upgrade to 10.4 and try those because I had seen reports of it working. I followed this tutorial and built the drivers from source like it said -[https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD"), and then used this tutorial to build my xorg.conf file. [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Everything seemed to be going smooth until I restarted and get a warning that says Error parsing config file, and also no drivers available.

I deleted the "ServerLayout" section from my xorg file and now when I restart I only get the "no drivers available" message before start up and have to run in low graphics mode. Any ideas?

Here's my xorg.conf file.

```
Section "Device"
        Identifier      "Radeon x1300"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon x1300"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes          "1800x1440" "1600x1200" "1280x1024" "1024x768" "800x600" "600x480"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

My system specs:
Dell Dimension C521 
2.5 GB RAM
Ati Radeon x1300
AMD Athlon 64 3200+
Ubuntu 10.4 32bit

Thanks :)

---

