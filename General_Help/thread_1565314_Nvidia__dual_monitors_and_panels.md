---
title: "Nvidia  dual monitors and panels"
date: 2010-08-31
forum: General Help
---

### Post by rmcellig on 2010-08-31
I just installed Wubi on my wife's PC and man is it fast!!! Wow. I set up Nvidia for her two monitors. The NEC monitor is the main one and the Dell monitor is the secondary one. My panels are showing up on the secondary monitor and not the main monitor. How can I fix this?

---

### Post by bodhi.zazen on 2010-08-31
> **rmcellig said:**
> I just installed Wubi on my wife's PC and man is it fast!!! Wow. I set up Nvidia for her two monitors. The NEC monitor is the main one and the Dell monitor is the secondary one. My panels are showing up on the secondary monitor and not the main monitor. How can I fix this?

I am not sure of the exact sequence, try running nvidia-settings and specifying which is the primary monitor.

```
gksu nvidia-settings
```

You may need to drag the panel to the correct location or set the panel location in preferences.

---

### Post by scouser73 on 2010-08-31
> **rmcellig said:**
> I just installed Wubi on my wife's PC and man is it fast!!! Wow. I set up Nvidia for her two monitors. The NEC monitor is the main one and the Dell monitor is the secondary one. My panels are showing up on the secondary monitor and not the main monitor. How can I fix this?

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by rmcellig on 2010-08-31
Thanks! Actually when I went into the Nvidia Settings GUI, the option to choose the main monitor was there so I cohose that and restarted my PC. Everything is fine now. Thanks anyway for the CLI solution.

---

### Post by hayhursm on 2010-09-22
> **scouser73 said:**
> You'll need to do this as root, so follow these instructions.
 
**1** - Paste this command into terminal: **gksudo nvidia-settings**
 
**2** - Click on **X Server Display Configuration**
 
**3** - Click on the monitor that you wish to make the main monitor
 
**4** - Check the box stating **Make This The Primary Display For The X Screen**
 
**5** - Click **Apply**
 
**6** - Click **Save To X Configuration File** & press **Quit**
 
***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***
 
[FONT=Times New Roman][SIZE=3]Hello,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]I am using Ubuntu Lucid x64 and have the Ubuntu restricted drivers installed for my Nvidia N250GTS.  I used the Nvidia GUI **(sudo nvidia-settings)** and selected my Samsung 22” LCD as the **Primary Monitor** but for some reason the login screen still appears on my Sharp 42” LCD (which I just use to watch movies).  Also, when I open Firefox it starts on the Sharp 42” instead of the Samsung 22”.  But Nautilus opens on the Samsung 22”, which is what I want every app to do...do you know why this inconsistency happens?  Is it possible I need to change something in XrandR instead of the nvidia-settings?[/SIZE][/FONT]

---

### Post by hayhursm on 2010-10-04
> **hayhursm said:**
> [FONT=Times New Roman][SIZE=3]Hello,[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I am using Ubuntu Lucid x64 and have the Ubuntu restricted drivers installed for my Nvidia N250GTS.  I used the Nvidia GUI **(sudo nvidia-settings)** and selected my Samsung 22” LCD as the **Primary Monitor** but for some reason the login screen still appears on my Sharp 42” LCD (which I just use to watch movies).  Also, when I open Firefox it starts on the Sharp 42” instead of the Samsung 22”.  But Nautilus opens on the Samsung 22”, which is what I want every app to do...do you know why this inconsistency happens?  Is it possible I need to change something in XrandR instead of the nvidia-settings?[/SIZE][/FONT]

Bump

---

### Post by brettreardon123 on 2010-12-25
I tried to do the steps using the nvidia settings, but I don't see the checkbox to set it as my default monitor. I'm completely lost, and my smaller monitor being my primary is really starting to bug me.

---

### Post by hayhursm on 2010-12-27
> **brettreardon123 said:**
> I tried to do the steps using the nvidia settings, but I don't see the checkbox to set it as my default monitor. I'm completely lost, and my smaller monitor being my primary is really starting to bug me.

I do not believe there is a "default monitor" option (hopefully they will add one in the future).  Under** X-Server Display Configuration** have you tried moving the monitors around under **Layout**?

---

