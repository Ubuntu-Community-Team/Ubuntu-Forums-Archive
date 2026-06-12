---
title: "Cant see contents of Iomega External hard drive"
date: 2010-02-24
forum: General Help
---

### Post by thesaintlyone@live.com on 2010-02-24
Hello Everyone complete newbie here!!!!

I have an Acer Aspire One running Ubuntu and IOmega External USB Hard Drive 250GB to make up for the 16GB on the netbook. both have been running fine until.......

Recently I had the Iomega plugged into a Windows XP Laptop which froze, I disconnected the Iomega and switched off the Laptop and rebooted, when I re plugged in the Iomega It failed to display any Items after a little bit of time and one or two shutdowns the Iomega worked fine on the XP

However when I plug the Iomega into the Netbook it appears under Files and folders but when I open it it just shows me a blank white screen.

Just to clarify I will need full instructions as I dont even know how to run Sudo!!!!!!

---

### Post by SecretCode on 2010-02-24
What is the file system on the external drive? I'm guessing ntfs.

If you have that XP laptop handy, plug it in there and run
```
chkdsk x: /f
```
from a windows command prompt. Substitute the drive letter it mounts as in place of x:.

---

### Post by thesaintlyone@live.com on 2010-02-25
Thanks for your reply....I tried it but noting happens!!!

---

### Post by SecretCode on 2010-02-25
Nothing? No messages, no error? That can't be right.

---

