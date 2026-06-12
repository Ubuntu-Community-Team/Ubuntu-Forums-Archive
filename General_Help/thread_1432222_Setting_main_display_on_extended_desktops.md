---
title: "Setting main display on extended desktops"
date: 2010-03-17
forum: General Help
---

### Post by pteri498 on 2010-03-17
Hi. I have extended desktop working on my netbook (finally, by turning off compiz), but now Gnome prefers my netbook's main screen as the main display (with the panel and such) instead of my external monitor.

How can I switch this? I don't see any setting for it in the Display dialog.

---

### Post by scouser73 on 2010-03-17
You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by pteri498 on 2010-03-17
Thank you for the very well-put list of instructions, however this is an intel video card, so I don't think it would apply to the nvidia-settings program. Unless I'm wrong.

---

### Post by petersfreeman on 2010-05-07
Try this, it worked for me:

[http://ubuntuforums.org/showthread.php?t=1329566&highlight=Primary+Display](http://ubuntuforums.org/showthread.php?t=1329566&highlight=Primary+Display)

Peter

---

