---
title: "Bars at top and bottom gone?"
date: 2010-03-21
forum: General Help
---

### Post by CycloneJoker on 2010-03-21
I've been running Xubuntu for the past month or two on my Acer Aspire One netbook with very few problems, and generally I've been happy.  But this morning, I went to boot up my netbook to check my email and when it booted, I got to my desktop, but the bars at the top and bottom of the desktop are missing.  I thought at first that it was hanging during the loading of Xubuntu and that there was a serious problem at hand that might've demanded a reinstall of Xubuntu, but upon further study once I got back to my campus, I discovered that the bars have simply disappeared and that everything else runs fine.  When I try to click "Panel" in "Settings", which I'm assuming is where I'd adjust settings for said bars, nothing comes up.

As I think about it, it doesn't seem like a major problem, considering everything else still seems to function fine, but I would like to have them back again.

Thoughts on the potential problem(s)?

---

### Post by Dantevus on 2010-03-21
This is just a shot in the dark but MAYBE your startup got messed up? Check the startup section and make sure the task controlling the bars is set to run on startup. Or start them up manually and have it save active sessions after you log off so they will always start up if there is no option there.

---

### Post by wilee-nilee on 2010-03-21
I have run into this with Xubuntu and there is a simple code you can run I hope this is it. Hold down alt and hit f2 the try this xfce-panel hit run then go to startup and save your session if the panels are back.

Try this command if that one doesn't work    
xfce4-panel
I think this is the correct one.

---

### Post by CycloneJoker on 2010-03-21
Ahh, thank you, xfce4-panel was the correct code.  I've added it back to the startup queue (hopefully in the correct way) so with luck I shouldn't have to deal with this for a while.

Thanks :D

---

