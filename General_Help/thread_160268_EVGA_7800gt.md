---
title: "EVGA 7800gt"
date: 2006-04-14
forum: General Help
---

### Post by f0rgiv3n on 2006-04-14
hey guys, i just installed ubuntu 5.10. I have a evga 7800gt, and my machine works with fedora 4 great, but when i get into the GUI with ubuntu, JUST after installing it, i mean, first log in, it asks me for my username/password i put them in and it gives me the loading screen showing what it's going to load and it plays the sound, but it freezes and gets scrambled. i'm pretty sure it has to do with my videocard do you guys have any idea how to fix this? it's not the physical videocard cuz it works great in windows/fedora etc... but, any ideas of how i can download the drivers for it off of nvidia's website through maybe the shell or something?! i'm not sure what the heck to do, help me if you can!

---

### Post by cilynx on 2006-04-17
Use the binary driver.  It appears that the built in 'nv' driver doesn't support the 7800gt properly.

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia")

---

### Post by xelink on 2006-04-27
I had a similar issue if not an identical one with my 7800GT. opt for the VESA drivers on install and then look into installing better drivers later.

---

