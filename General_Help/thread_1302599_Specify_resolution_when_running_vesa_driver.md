---
title: "Specify resolution when running vesa driver"
date: 2009-10-27
forum: General Help
---

### Post by nikgare on 2009-10-27
Hi,
I've got a headless box running Jaunty.  To make it boot up into the desktop I've had to edit the xorg.conf file to specify the vesa driver, but can't specify the resolution.
What ever I try the desktop will default to 800x600, and if I open up the Display Preferences I can only select 800x600 or 680x480.
I'd ideally like something a bit bigger than that!

Here is my xorg.conf file
```

Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device" 
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

```

It doesn't seem to make any difference what I put in the Modes section, the machine always boot to 800x600.
What am I doing wrong?

---

### Post by martrn on 2009-10-27
> **nikgare said:**
> .....I've got a headless box running Jaunty.  ..[...]... 800x600 or 680x480. I'd ideally like something a bit bigger than that! ... [...] ... [...] ...It doesn't seem to make any difference what I put in the Modes section, the machine always boot to 800x600. What am I doing wrong?

You need to install the correct driver for the graphics card.  I belive you are possible the wrong graphics driver for the machine, but I don't understand why you would want to change the resolution if you are booting your machine and running it headerless.

Follow the instructions on writing your Xorg.conf file as your video graphics chard manufacture states, otherwise you are stuck with [https://wiki.ubuntu.com/BulletProofX]("https://wiki.ubuntu.com/BulletProofX")'s reduced vessa mode.

---

