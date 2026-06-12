---
title: "How to disable suspend in Ubuntu 12.04"
date: 2012-05-06
forum: General Help
---

### Post by Canaryguy on 2012-05-06
Hello,

I'm using Ubuntu 12.04 x64 on a laptop with Unity and KDE desktops. Both in Unity and KDE power settings I have disable the supend option but when I close the lid the system suspends and when I open the lid again the system is frozen, just a black screen so I have to force a shutdown. So, is there any way of disabling the suspend process?

Thanks.

---

### Post by wilee-nilee on 2012-05-06
In the power app are drop-downs for lid closure, one plugged in, one on battery power.

---

### Post by Paqman on 2012-05-06
You can probably also completely disable suspend in BIOS.

---

### Post by Canaryguy on 2012-05-06
In both in battery mode or plugged in I have chosen Do not suspend (when the system is inactive) and Do nothing (when the lid is closed) but even though the system suspends when I close the lid.

---

### Post by Canaryguy on 2012-05-06
> **Paqman said:**
> You can probably also completely disable suspend in BIOS.

There isn't such an option in the BIOS :-(

---

### Post by Canaryguy on 2012-05-06
I have to add something.

If I just lock the screen and close the lid the system does not suspend.

If instead of "locking the screen" I choose "switch user account..." then I go to the initial screen for users to log in and here if I close the lid the system will suspend and that's what I want to avoid.

---

### Post by YMS_1975 on 2012-05-07
> **Canaryguy said:**
> In both in battery mode or plugged in I have chosen Do not suspend (when the system is inactive) and Do nothing (when the lid is closed) but even though the system suspends when I close the lid.

I have the exact same problem. This only started with 12.04 LTS. Did not have this problem before.

For anybody reading this that needs more specific info. I've got an MSI GX-720 laptop, 4 GB Ram, Intel Core 2 Duo P8600 @ 2.40 GHz x 2.
64 Bit OS.

And my settings are the same as his (I checked the power app).  :(

---

### Post by Radical Thought on 2012-05-08
Possible workaround:  In System Settings > Brightness and Lock switch off 'Lock'. The downside is that your system also cannot lock anymore after a set time.

---

### Post by conualfy on 2012-05-08
I get the same reaction, but not all the times. Most of the times I can come back from suspend, but sometimes I just have to force a shut down. I think this should be a separate bug report.


I reported the the lock screen bug here: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/995840/](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/995840/)
Please subscribe the bug and help showing the developers it is an important bug.

Thanks!

> **Canaryguy said:**
> Hello,

I'm using Ubuntu 12.04 x64 on a laptop with Unity and KDE desktops. Both in Unity and KDE power settings I have disable the supend option but when I close the lid the system suspends and when I open the lid again the system is frozen, just a black screen so I have to force a shutdown. So, is there any way of disabling the suspend process?

Thanks.

---

### Post by YMS_1975 on 2012-05-08
> **Radical Thought said:**
> Possible workaround:  In System Settings > Brightness and Lock switch off 'Lock'. The downside is that your system also cannot lock anymore after a set time.

I tried your fix but it didn't work. The only difference though, was that when I opened my laptop again it was not completely black. I could see my desktop & the respective icons.

Unfortunately I was unable to move my mouse around (everything was frozen).
This sucks. I hope they fix it fast.  :p

---

### Post by Radical Thought on 2012-05-09
I think Canaryguy and YMS_1975 are effected by something else as I and conualfly are. My system does not crash. The only problem I have is that I am asked for a password after opening the lid while I specified "do nothing". So I only suffer unexpected behavior.

---

### Post by Canaryguy on 2012-05-09
> **Radical Thought said:**
> I think Canaryguy and YMS_1975 are effected by something else as I and conualfly are. My system does not crash. The only problem I have is that I am asked for a password after opening the lid while I specified "do nothing". So I only suffer unexpected behavior.

Go to **System Setting > Brightness and lock** and untick the last option. That will avoid asking for a password when the computer wakes up after suspend.

---

