---
title: "Random Xorg failures"
date: 2011-05-04
forum: General Help
---

### Post by bouncingwilf on 2011-05-04
I would like to canvas a little advice here if I may as I need to go "remote bug hunting" and will need all the tips I can get!

The system is a remote one (300 miles away) with computer illiterate user and no ssh link and experiences random occasional xorg (I think) failures. Sadly, this always seems to happen when the user is out of cell phone range of land and the symptoms are (as quoted by the user) "A black box comes up and says the computer has gone into low graphics mode". Generally, the only way he understands to get rid of the box is to crash the computer and restart.  

Now the technical stuff:

The box comprises an Intel D510MO motherboard, 1gb ram and a 160gb sata hard drive running Maverick Meerkat. The screen is a simple xvga 15" monitor and the application that is possibly the source of the problem is DrDepth, a Windows application running under wine 1.2. This application does not use any openGL or DirectX etc - just writes to a standard windows video context. There are no other user apps running.


Now I realize that the problem description is inadequate but what I'm hoping for is tips of where to look. whatever the problem is, its' apparently random and reasonably infrequent. Anyone any ideas?


Bouncingwilf

---

