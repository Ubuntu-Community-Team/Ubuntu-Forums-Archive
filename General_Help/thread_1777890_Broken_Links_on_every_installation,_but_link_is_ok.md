---
title: "Broken Links on every installation, but link is ok when I see it in Nautilus"
date: 2011-06-08
forum: General Help
---

### Post by pizzaia on 2011-06-08
Hi, I'm a new user of linux. After a few times that I screw up everything, I reinstalled Linux, in a new Partition, just formatted. Now, when I try to install, or copy, into my /usr/local/"whatever" folders I just see broken links of the files (the little x in the right top of the file, I presume is a broken link). But when I see the file in nautilus, the files seems to be good. But the programs doesn't works. The programs I've been installing are NukeX and UV Layout. The weird thing is that the very first time I installed Linux everything worked smoothly. Since I formatted the partition I've only unistalled Noveau and installed the Nvidia latest drivers of my GPU.
I will apreciate if you could provide me any help.
Thank you!

---

### Post by jerrrys on 2011-06-08
click on a broken link and see if it tells you anything (maybe an error msg).  sounds like maybe a permission problem.  if thats the case you can open a terminal and enter **gksudo nautilus** and see what happens.

---

### Post by pizzaia on 2011-06-08
I've solved the Issue, the problem was that I had not the 32 bit libs installed. Thanks anyway

---

