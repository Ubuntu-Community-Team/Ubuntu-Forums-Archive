---
title: "Screen Resulotion"
date: 2006-06-01
forum: General Help
---

### Post by sbrinkmann on 2006-06-01
Hello,
    i have installed Dapper Drake on my Dell Inspiron 6400. My Notebook has WXSGA Display with the maximum Screen Resulotion is "1680x1050"

The System is running only in "1280x1024" and i can't change the Resulotion.

**This ist my "etc/X11/xorg.conf"**
```

Section "Device"
        Identifier      "Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

```

What should i change or install to change the Screen Resulotion to "1680x1050".

---

### Post by GazaM on 2006-06-01
Go into Synaptic and install a package called 915resolution. Then read the instructions in the file /usr/share/doc/915resolution/README.Debian

The only thing you might have to do which deviates from the instructions is use sudo for the 915resolution commands. After this, it'll run automatically on every boot and you won't have to worry about it.

I heard that this fix was going to be implemented in the actual i810 driver a while ago, not sure on the status of that to be honest. I hope it happens for the next release, as this is a big annoyance for a lot of laptop users trying Linux on them for the first time.

---

