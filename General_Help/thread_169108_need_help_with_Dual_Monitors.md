---
title: "need help with Dual Monitors"
date: 2006-05-01
forum: General Help
---

### Post by kentshultz on 2006-05-01
Hello all.  My name is Kent and I am new to Ubuntu and to these forums.

I just installed Breezy on my amd64 system and installed the latest nvidia driver from the repositories.  However, I can't seem to get my second monitor working.  I am running both monitors from ONE videocard (an Nvidia 6800GT, one VGA, one DVI port).  I have tried tinkering with my xorg.conf a little bit, but have had no success.  I've tried adding a second "Monitor" section, a second "Screen" section, and referencing their relative positions in the "ServerLayout" Section (e.g. "Default Monitor" LeftOf "Secondary Monitor").

I hope this is the right approach to enabling my second monitor and if it's not, please let me know!  Otherwise, can anyone help me with the configuration of my xorg.conf?

Any advice is appreciated :)

---

### Post by Scunizi on 2006-05-02
I'm in almost the same boat... I've got a 6600gt turbo with the same type of outputs.  I delved into nVidia's site and they have a lot of assistance there but I haven't had the time to read and play.. Hopefully a more straightforward solution will popup here!

Edit:  I just noticed this thread was started in the Warty section.  kentshultz, are you running Warty, Breezy or Dapper...? I'm on Dapper B

---

### Post by kentshultz on 2006-05-02
[QUOTE=Scunizi]I'm in almost the same boat... I've got a 6600gt turbo with the same type of outputs.  I delved into nVidia's site and they have a lot of assistance there but I haven't had the time to read and play.. Hopefully a more straightforward solution will popup here!

Edit:  I just noticed this thread was started in the Warty section.  kentshultz, are you running Warty, Breezy or Dapper...? I'm on Dapper B[/QUOTE]

Whoa, I'm not sure how I got into the Warty forums... I am running Breezy.  Maybe we should go over to another forum...

Anyway, I sort of got my dual monitors working.  I found a helpful thread somewhere else on the forums and I took some pieces from someones xorg.conf.  Here's is the relevant portion of my xorg.conf:
[B]
Section "Device"
        Identifier      "6800GT 1"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen 0
EndSection

Section "Device"
        Identifier      "6800GT 2"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen 1
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "SyncMaster 2"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "6800GT 1"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Secondary Screen"
        Device          "6800GT 2"
        Monitor         "SyncMaster 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "DualHead Layout"
        Screen  0       "Default Screen" 0 0
        Screen  1       "Secondary Screen" RightOf "Default Screen"
        Option          "Xinerama" "on"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection



[/B]

I'm not entirely sure what Xinerama is or what it does, but the functionality I now have is similar to "Dual View" with Nvidia Windows drivers.  That is, an open window will NOT span accross both monitors when you maximize it.  Just how I like it :)

However, Xinerama has messed a little with X or something.  For example, I am unable to change my resolution now (not that I want to).  If I try to, there is an error:

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."

So I don't know, might still need some work.  And Nvidia settings (nvidia-settings) doesn't show up with 2 monitors.

Oh, also, this may be kind of newb question... Would running dual monitors be any easier or harder (or different at all) with KDE?

---

### Post by ihavenoideax2 on 2006-05-04
I'm wondering if i can setup dual monitors with sli. I'm using 2 6600GT PCIe cards. Ive been trying to do this for a while.

---

### Post by Scunizi on 2006-05-06
I've just found a link that explains alot in fairly simple terms.  It tells of the differance of Twinview and Xinerama and gives 3 possible setups depending on what you're trying to accomplish.  The option the author prefers is #3 which uses Xinerama and allows a window to maximize on one screen without spanning across to the other.  I think it also allows different resolutions on each monitor.  It's set up for one CRT and one DFP (DVI) monitor off one card.  [http://gentoo-wiki.com/Twinview_Example#Introduction]("http://gentoo-wiki.com/Twinview_Example#Introduction")

I'm beginning to play with it and will post my end results when I'm happy with the results.

---

### Post by Scunizi on 2006-05-06
Like Kent, I got my dual monitors working.  I followed the link in my previous post with a little augmentation.  I've noticed the background on the desktop spans both monitors.  However, windows stay on their monitor when maximized.  I also can't change the resolution.  In fact, when I load nvidia-settings it doesn't even show my second monitor.  If I've done this right there'll be two attached files, my original xorg.conf without dual monitor support and my current setup that allows both monitors.  For those still searching it might help.  There are also some glairing differances from Kent's functional setup and mine.  I'm almost happy now.  Unfortuantly, with what I've learned I'm going to have to dive in and play some more!:rolleyes:

---

