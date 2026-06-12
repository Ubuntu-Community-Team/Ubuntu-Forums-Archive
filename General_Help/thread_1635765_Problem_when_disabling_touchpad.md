---
title: "Problem when disabling touchpad"
date: 2010-12-02
forum: General Help
---

### Post by Magus_Stragus on 2010-12-02
Good day. I was trying to disable the synaptics touchpad while typing using the guide found in the help section (which, oddly, I can't find anymore. Maybe an update?)

Any roads, I modified the xorg.conf file in /etc/X11/ (actually, I created it as it was missing in my files), and put on it a line similar to this:

    Section "InputDevice"
    Identifier "Synaptics Touchpad"
    ...
    Option "SHMConfig" "on"
    End Section 

After I reboot, I receive a message saying that there was a problem and Ubuntu is now running on low graphics mode. 

And, I still can't fix what I wanted to fix. Any other way to disable the synaptics touchpad while typing? I also tried to go to System>Preferences>Touchpad, but it tells me that GSynaptics couldn't be initialized and that I need to turn SHMConfing on "true" on xorg.conf. (Just what I did and caused me the graphics problem).

Any help, please?

---

### Post by ajgreeny on 2010-12-02
Instead of
```
Section "InputDevice"
    Identifier "Synaptics Touchpad"
    ...
    Option "SHMConfig" "on"
    End Section 
```
try
```
Section "InputDevice"
     Identifier "Synaptics Touchpad"
     ...
     Option "SHMConfig" "True"
     End Section 
```
I'm not certain if it matters if the word is "true" or "True", both appear in my xorg.conf, so both may work, for all I know.

---

### Post by Magus_Stragus on 2010-12-02
Nope, that didn't work. Same graphics problem at bootup.

---

### Post by Magus_Stragus on 2010-12-04
No one else can give me a hand with this?

---

### Post by Magus_Stragus on 2010-12-29
Could someone please help me out with this? I've tried many guides on the net but none has worked. Many of them refer to a xorg.conf file (in a X11 directory in /etc), but that file is missing! A blank page appears when I try to edit it, and if I do, I have problems restarting. 

What should I do? This is getting extremely annoying and I'm really desperate for solution!

---

### Post by hawthornso23 on 2010-12-29
The method you describe doesn't work on my laptop (Latitude E6510) because the touchpad on that model of laptop is misidentified as a PS/2 Generic Mouse. It isn't treated as a touchpad at all! I therefore use an alternative method on my Dell to disable the touchpad when typing.

Firstly open a terminal.

```
xinput --list
```

will tell you what input devices you have. You should be able to guess what your touchpad is. Mine turned out to be the aforementioned PS/2 Generic Mouse. I then disable it with 

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0
```

and reenable it with 

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1
```

If this works, it is simple enough to set keyboad shortcuts to these commands and enable/disable your touchpad with a simple key combination. Not as convenient as proper "disable during typing" which happens automatically whenever you start to type - but a workable solution.

I mention this method on the chance that your laptop is a DELL latitude in which case the other method isn't going to work.

---

### Post by Magus_Stragus on 2011-01-04
Hmm... Thanks, that worked, although not as good as I would have expected in the end for a solution. Still, it's better than nothing for the time being. 

Any one else have a solution to this problem?

---

