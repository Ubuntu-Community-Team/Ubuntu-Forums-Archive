---
title: "Startup programs doesn't run"
date: 2010-02-03
forum: General Help
---

### Post by thezood on 2010-02-03
I have the weirdest issue that I first thought was a Lucid Alpha issue. I have now reinstalled Karmic, created a new home folder and the problem remains. My /home is on a separate ext3 partition and / is on ext4.

The problem is that none of my startup applications runs when I start my computer. I have to run nm-applet, empathy etc. every time. I have tried removing and restoring my home folder, changed ownership and mod with no result. I have no problems reading or writing to my home folder. 

I did mess up during experimentation some time ago and started X with no write access to my home folder but that shouldn't matter since I restored access and restarted X, right?

Does anyone have any idea as to why this happens and how to fix it?

---

### Post by thezood on 2010-02-03
Reinstall and a complete cleanup of my messy home folders solved this issue. Too many experiments made jack a dull boy.

---

