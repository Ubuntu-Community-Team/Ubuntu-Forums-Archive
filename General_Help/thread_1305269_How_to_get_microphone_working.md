---
title: "How to get microphone working"
date: 2009-10-29
forum: General Help
---

### Post by Crash~Override on 2009-10-29
Hey guys, I installed ubuntu netbook remix 9.10 karmic this morning on my asus 1005ha and i was wondering how do i enable the microphone on this?

Please help...

---

### Post by frdrx on 2009-10-29
Installing the package [FONT="Courier New"]linux-backports-modules-alsa-karmic-generic[/FONT] helped in my case.

---

### Post by Crash~Override on 2009-10-29
okay I will try and report back soon

---

### Post by Crash~Override on 2009-10-30
> **frdrx said:**
> Installing the package [FONT=Courier New]linux-backports-modules-alsa-karmic-generic[/FONT] helped in my case.

actually this worked like a charm! Now i have a fully working ubuntu 9.10 UNR on my asus 1005ha!

I am loving it better than xp or windows 7 right now!

Thanks frdrx
Love this community!

Go Ubuntu :p

---

### Post by jbcfarina on 2009-10-31
I got the same problem, and the recorder works, but Skype don't, only works with an external mic, any suggestions?

I gonna try empathy, :-)

---

### Post by 6205 on 2009-10-31
> **jbcfarina said:**
> I got the same problem, and the recorder works, but Skype don't, only works with an external mic, any suggestions?

I gonna try empathy, :-)

I have switched to microphone 2 to get Skype working

---

### Post by kjaspan on 2009-10-31
I installed Karmic on 10/29/2009 and am unable to get Skype to work with my Logitech headset, though it did work fine with Jaunty. The Sound Preferences window now lacks an "Apply" button (only Close) and Skype does not find my headset. Have also never got my Logitech Quickcam Connect to work, either with Jaunty or Karmic.

lsusb output:
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:089d Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Screenshot attached

---

### Post by kjaspan on 2009-10-31
Problem solved. System -> Preferences -> Sound seem to have little or no bearing on Skype usage. In the Skype Options menu, the settings as in the screenshot attached hereto fixed the problem.

Webcam is another hill to climb!

---

### Post by jbcfarina on 2009-10-31
I don't know if I should start a new thread, but in my ASUS I can't see other device to choose. The funny thing is the gnome-sound-recorder works with the internal mic.

PD: entrada = input in Spanish

---

### Post by Kubureaucrat on 2009-10-31
On my config I only have Pulse audio server (local), nothing else.

Nothing from my mic through skype or elsewhere since the karmic upgrade.

---

