---
title: "Dual Monitor flash question"
date: 2010-06-09
forum: General Help
---

### Post by Jahe25 on 2010-06-09
I'll admit I'm using Mint rather than Standard Ubuntu at the moment, but no-one on the Mint forums seems to be able to help, so I'm hoping the lovely people here would oblige, cos had this same problem when I was using Ubuntu.

I have a laptop attached to a secondary monitor. In Windows, if I have  my browser on my second monitor and go full screen in youtube or BBC  iPlayer or whatever, it fills the second monitor screen, but in Mint/Ubuntu,  regardless of what monitor the browser is on, it always fills the laptop  screen. It's kinda inconvenient having to turn off my laptop screen  whenever I want to watch something in fullscreen on the bigger monitor  so i was wondering if there was any way to sort this. Cheers in advance

---

### Post by scouser73 on 2010-06-10
You need to make the external monitor as the primary monitor.  I can offer you help doing this if you have Nvidia graphics card, any other card and I wouldn't know.

**_Selecting a primary monitor_**

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by vahnx on 2010-06-10
Is there another way to do this, as there should be no need to do this in a "modern" distro. I want my laptop to remain primary, as it does in Windows/OSX.

---

### Post by Jahe25 on 2010-06-10
I typed 'gksudo nvidia-settings' into the terminal, and I get a thing in the bottom panel saying 'Starting Administrative Application', then that goes away and I get nothing more.

Does this mean I don't have nvidia graphic card? Now that I think about it, I vaguely remember there being an ATI Radeon sticker on my laptop when I bought it =/

---

### Post by ub-newbie on 2010-06-10
try "dmesg | grep nvidia" as a quick-n-easy way to see what driver you have installed (I don't have MINT, so not sure if this will work for you).

---

### Post by unSinn on 2010-06-27
Hi, same problem here.
Unfortunately the solution does not help me as I have an AMD/ATI-Card 5850.
Flash in Fullscreen always opens on my small "secondary" screen on the left...

thanks

---

