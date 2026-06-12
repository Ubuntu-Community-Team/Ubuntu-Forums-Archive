---
title: "Monitor output won't turn back on"
date: 2012-07-26
forum: General Help
---

### Post by djuke04 on 2012-07-26
Hello,
  I searched and could not find any threads with quite this issue, and tried some other solutions to no success.  The fresh install of 64-bit 12.04 boots fine from SSD, outputting from nvidia gts250 graphics card via hdmi to a receiver that switches signals to a television.  If anything happens to the signal, it seems to not shake hands again and agree with either the receiver or the tv, and no signal is output (the tv turns to powersaver mode, or stays black screen).  This could be due to:

1) inactivity - I left the computer running and it timed the monitor to sleep (this has since been disabled)

2) the tv and receiver were turned off
3) the input on the receiver was switched to a different source
4) switch to terminal (alt-ctrl-f1, etc) - doesn't ever switch, screen just goes black
5) the system was suspended or hibernated, it won't resume as it should, but instead is blank/black

A few times, when I've been trying to shut it down with some key strokes rather than the power button (a restart is the only solution to get the monitor back on), I logged out of the gui, and for some reason the display started again.  I cannot replicate this reliably with any sequence of hotkeys or keystrokes.  

What I've tried so far mainly involves the nvidia driver.  I added a repository, updated, upgraded - nothing.  so then I tried to use an older version, nothing.  Via "additional drivers" I tried both options.  Nothin in the x server settings seems obvious to change.  current driver version is 295.40.  Under "Display configuration" it says "Unable to load x server display configuration page: The NVIDIA X driver on HTPC:0.0 is not new enough to support..." - not sure if that's relevant.

Basically, if I want to use the computer I can't leave it without leaving everything on, or when I try to turn the screen on, it's blank, if I switch away from the pc source on the receiver, it's blank when I come back to it, and if the system turns of the monitor from inactivity, it's blank when I'm active again.  

what could be causing this?  Thanks for your time and assistance, I appreciate it!

---

### Post by dartmusic on 2012-08-28
Not terribly helpful I know, but wanted to say that I have a similar problem. I can get to the Nvidia X server settings but other than turning off Power Mizer (which did nothing) I see no options related to this. 

Pulling the HDMI from the computer and replacing it usually "wakes" the display. 

I'll post if I can find anything useful. 


> **djuke04 said:**
> Hello,
  I searched and could not find any threads with quite this issue, and tried some other solutions to no success.  The fresh install of 64-bit 12.04 boots fine from SSD, outputting from nvidia gts250 graphics card via hdmi to a receiver that switches signals to a television.  If anything happens to the signal, it seems to not shake hands again and agree with either the receiver or the tv, and no signal is output (the tv turns to powersaver mode, or stays black screen).  This could be due to:

1) inactivity - I left the computer running and it timed the monitor to sleep (this has since been disabled)

2) the tv and receiver were turned off
3) the input on the receiver was switched to a different source
4) switch to terminal (alt-ctrl-f1, etc) - doesn't ever switch, screen just goes black
5) the system was suspended or hibernated, it won't resume as it should, but instead is blank/black

A few times, when I've been trying to shut it down with some key strokes rather than the power button (a restart is the only solution to get the monitor back on), I logged out of the gui, and for some reason the display started again.  I cannot replicate this reliably with any sequence of hotkeys or keystrokes.  

What I've tried so far mainly involves the nvidia driver.  I added a repository, updated, upgraded - nothing.  so then I tried to use an older version, nothing.  Via "additional drivers" I tried both options.  Nothin in the x server settings seems obvious to change.  current driver version is 295.40.  Under "Display configuration" it says "Unable to load x server display configuration page: The NVIDIA X driver on HTPC:0.0 is not new enough to support..." - not sure if that's relevant.

Basically, if I want to use the computer I can't leave it without leaving everything on, or when I try to turn the screen on, it's blank, if I switch away from the pc source on the receiver, it's blank when I come back to it, and if the system turns of the monitor from inactivity, it's blank when I'm active again.  

what could be causing this?  Thanks for your time and assistance, I appreciate it!

---

