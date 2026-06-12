---
title: "Remote Desktop Problems"
date: 2011-01-30
forum: General Help
---

### Post by Mindkontrol on 2011-01-30
I am trying to setup a headless box running Ubuntu 10.10 and am wanting to be able to remotely use it from my windows 7 machine. I had is setup fine using the remote desktop options in Ubuntu and running VNC on Win7. Was working like a charm, fast response time with little lag. Now for some reason it has slowed WAAAY down to the point where it is unusable. I can gain access to the Ubuntu system, but my VNC window is not showing the things happening on the Ubuntu box. I can click in the VNC window and see the commands happening on my Ubuntu monitor in real time, yet the VNC window does not reflect this. The only thing ive really done since it was fast was to setup ssh so that i could terminal in from a virtual Ubuntu on my Win7 machine. Not sure if this somehow affected my settings for Remote Desktop or what, tho I have tried the RD connection after disabling the ssh server and it didnt help at all. Just FYI I check the forums for related topics before posting, but my situation seemed unique as it WAS working fine and now is not. Thanks in advance for any and all help.

---

### Post by Mindkontrol on 2011-01-31
bump

---

### Post by derklempner on 2011-01-31
This is a well-known issue between Compiz and Remote Desktop.  The easiest workaround is to disable Remote Desktop and install another VNC client, such as **x11vnc**.

I had the exact same problem on all of my Ubuntu systems, and I've switched over to **x11vnc** and have no more issues with the remote desktop not updating correctly.

---

### Post by Mindkontrol on 2011-01-31
Hmm, Just so strange that it was working like a charm not long ago.

---

