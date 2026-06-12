---
title: "DVI stopped working"
date: 2009-09-12
forum: General Help
---

### Post by measekite on 2009-09-12
I have been using Jaunty running a BFG 6600 for a couple of months connected to a ViewSonic monitor.  I shut down my computer to replace a mouse.

Upon reboot the got a black screen after the splash screen.  I then connected the VGA cable to the analog port on the card and it worked.  I do not know what to do now to get DVI.

Here is what I did so far.

Reinstalled Nvidia drivers.  But I cannot save the configuration file which is owned by root from the Nvidia panel.  The error says cannot make a backup and cannot write to the file.

I can edit it by hand but do not know what to do.

Any help on this.

---

### Post by synapsys on 2009-09-12
I'm not sure if this will help, but you can access the nvidia control panel (with root priveleges) from the command line by typing:

```
gksu /usr/bin/nvidia-settings
```

---

### Post by measekite on 2009-09-12
> **synapsys said:**
> I'm not sure if this will help, but you can access the nvidia control panel (with root priveleges) from the command line by typing:

```
gksu /usr/bin/nvidia-settings
```

That allowed me to save but did not solve the problem.

Here are more tests that I did.

I booted from the Live CD.  I could then get either DVI or Analog depending on how I set my monitor.  I was using nvidia 180 drivers.

I then restarted from my hard disk.  I uninstalled nvidia drivers.  I then reinstalled nvidia 180 drivers from Admin>Hardware drivers.  It did not work.   I could not switch from Analog to DVI.

Does anybody have any ideas on how to do this?

---

### Post by 3rdalbum on 2009-09-12
A friend of mine had this symptom. It was a hardware problem; the monitor's DVI board was dead. Try the monitor in another computer; if it still doesn't work then it's the monitor.

If it does work, then try putting the graphics card in another computer, and then try using a different monitor cable.

---

### Post by measekite on 2009-09-13
> **3rdalbum said:**
> A friend of mine had this symptom. It was a hardware problem; the monitor's DVI board was dead. Try the monitor in another computer; if it still doesn't work then it's the monitor.

If it does work, then try putting the graphics card in another computer, and then try using a different monitor cable.

I believe that both the graphics card and the monitor are ok.  Here is the reason why.  I booted from the Live CD and I was able to get both DVI and Analog from the system.  It just does not work when booting from the hard disk.

---

### Post by measekite on 2009-10-10
> **3rdalbum said:**
> A friend of mine had this symptom. It was a hardware problem; the monitor's DVI board was dead. Try the monitor in another computer; if it still doesn't work then it's the monitor.

If it does work, then try putting the graphics card in another computer, and then try using a different monitor cable.

Remember that when booting with the LiveCD and installing the 180 driver BOTH DVI and VGA worked.

Also I did a complete uninstall including the configuration files in Synaptic and then reinstalled with Synaptic.

I did a cold reboot.  I saw that it started digital.  I then saw the splash screen with the bar underneath the U B U N T U going across.  It still was digital.  It then switched to analong just when the logon screen came up and could not get dvi after than.

The fact that I was getting digital until the logon screen tells me that the monitor and card are not the problem.  I think the uninstall is missing a file or two and new install does not overwrite it but which one and where?

Ideas are welcome.

---

