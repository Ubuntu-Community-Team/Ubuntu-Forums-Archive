---
title: "How do I permenently change folder permissions?"
date: 2009-11-11
forum: General Help
---

### Post by Dustin2128 on 2009-11-11
Fixed my warcraft problem earlier by allowing folder access, but now I've got some patches to apply and the warcraft folder keeps locking down to where I can't access it, and it makes the desktop icon completely useless. any suggestions?

---

### Post by scouser73 on 2009-11-11
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by Dustin2128 on 2009-11-11
mm, thanks, I'll finish playing warcraft in a few and get right on it. It's fun to see people on the game who think running warcraft/linux is impossible, I need to make a video.

---

### Post by krakenfury on 2009-11-11
Virtualbox?

---

