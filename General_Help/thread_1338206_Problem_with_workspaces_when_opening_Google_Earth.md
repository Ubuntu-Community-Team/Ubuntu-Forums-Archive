---
title: "Problem with workspaces when opening Google Earth"
date: 2009-11-26
forum: General Help
---

### Post by Yumi on 2009-11-26
When I open Google-Earth all open windows in all workspaces are moved to workspace 1. What causes this wired behaviour?

OS ubuntu karmic

Michael

---

### Post by ene_dene on 2009-11-26
> **Yumi said:**
> When I open Google-Earth all open windows in all workspaces are moved to workspace 1. What causes this wired behaviour?

OS ubuntu karmic

Michael
You are running desktop effects, when you run google earth your desktop effects shutdown for some reason and when that happens all the windows jump to workspace 1.
My suggestion is that you go to system-> preferences->appearance->visual effects and select "none". When using other 3D software, in mine experience desktop 3D effects usually cause pain.

---

### Post by Yumi on 2009-11-26
Thank you for the quick reply. But visual effects was set to none. Apart from the number of workspaces it is a pretty standard nofrill installation.

Michael

---

### Post by ene_dene on 2009-11-26
> **Yumi said:**
> Thank you for the quick reply. But visual effects was set to none. Apart from the number of workspaces it is a pretty standard nofrill installation.

Michael
The change of workspaces happens when you you set from "normal/extra" to "none". Maybe it was on "normal" and when you started google earth it turned to "none".
Try this, set it to "none" and then put few windows on few workplaces and then start google earth. Does the problem happen again? If so, then I don't know what is the problem.
I'm telling you this because I had the exactly the same problem few Ubntus ago and since then I always put it to "none". When you install new graphic drivers or something it's put to "normal".

---

### Post by Yumi on 2009-11-26
Your last description hit the nail on the head. I followed the instructions and the problem is solved. 

No issue for Ubuntu, it is Google who is beheaving in a odd way.

Thanks a lot 

Michael

---

