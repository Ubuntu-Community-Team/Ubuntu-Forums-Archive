---
title: "Ubuntu + Gnome + dual monitors/screens"
date: 2010-10-21
forum: General Help
---

### Post by hecht on 2010-10-21
Hi

Recently I connected second monitor to my laptop. Everything seems ok. I got what i wanted: extended working space, panel on second monitor with windows list that are present on corresponding screen.
One thing  that is annoying me is GDM. It displays login dialog on my second LCD not laptop. Is there a way to make GDM to display login dialog window on my laptop or how to designate laptop LCD as primary screen or something?

tnx
(ubuntu 10.10)

---

### Post by scouser73 on 2010-10-21
> **hecht said:**
> Hi

Recently I connected second monitor to my laptop. Everything seems ok. I got what i wanted: extended working space, panel on second monitor with windows list that are present on corresponding screen.
One thing  that is annoying me is GDM. It displays login dialog on my second LCD not laptop. Is there a way to make GDM to display login dialog window on my laptop or how to designate laptop LCD as primary screen or something?

tnx
(ubuntu 10.10)

Assuming that your graphics card is from nVidia, then follow the instructions.

You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by hecht on 2010-10-21
Sorry I forgot to tell you that my graphic card is 
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
as I can remember some x4500
So no nvidia solution will work here I presume...

---

### Post by chaanakya_chiraag on 2010-10-21
That is correct.

However, there may be a similar option in Monitors.  I am not familiar with it myself as I have always had nVidia graphics cards.

---

