---
title: "Compiz Will Not Start"
date: 2010-01-25
forum: General Help
---

### Post by Joseph Schwenker on 2010-01-25
When I turned on my computer today, Compiz would not start.   I tried launching it from the terminal, and this is what I got: 

```
joseph@joseph:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Segmentation fault
Window manager warning: "" found in configuration database is not a valid value for keybinding "activate_window_menu"
Window manager warning: "" found in configuration database is not a valid value for keybinding "unmaximize"
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x4000023 (Untitled -); these messages lack timestamps and therefore suck.

```

Does anyone have any ideas as to why it isn't working?  I urgently need this fixed, as Compiz is VERY important to my workflow.  I am running Ubuntu 9.04 32-bit, and my nVidia Card's restricted drivers are enabled.

---

### Post by Joseph Schwenker on 2010-01-25
By reinstalling the package "compiz" I was able to restore Compiz to a working state.  If this happens in the future, what can I do to solve it?  What caused this problem in the first place?

---

### Post by ibuclaw on 2010-01-25
Try this debugger script: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)
That should give you an idea why it is going wrong.

Paste the output of that script into your next post.

Regards
Iain.

---

### Post by Joseph Schwenker on 2010-01-25
Now that I have reinstalled Compiz, your script "compiz-check" outputs this: 
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by ibuclaw on 2010-01-25
> **Joseph Schwenker said:**
> Now that I have reinstalled Compiz, your script "compiz-check" outputs this: 
```
Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```
It isn't my script, but since everything seems OK, I'll just mark this thread as solved, if you don't mind. :)

Regards
Iain

---

### Post by Joseph Schwenker on 2010-01-25
Thanks for your help.  Although, I am still not sure why this happened in the first place.

---

### Post by Ed4 on 2010-01-28
I experienced the same issue.  Compiz was working fine until some recent update, and now it doesn't start.  It took me a little while to notice what had happened, since the system falls back to metacity automatically.  Here is the output of the compiz-check script:   ```
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G92 [GeForce GTS 250] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 
```

---

### Post by Ed4 on 2010-01-28
The problem went away when I upgraded the nvidia binary driver from 190.42 to 190.53.

---

