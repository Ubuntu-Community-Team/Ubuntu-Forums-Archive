---
title: "mount.ntfs problem with Wubi install"
date: 2011-11-06
forum: General Help
---

### Post by stfnmchr on 2011-11-06
Hi,

Is anyone else having problems with "mount.ntfs" process? Everytime I do something that involves heavy disk usage, the process mount.ntfs eats up 100% of my cpu and makes my Asus 1215b virtually unresponsive. I've searched the Internet for any solution but it seems the general consensus is that it is the driver's fault and nothing can be done for the time being. I'm heartbroken because that makes using Ubuntu a heavy burden and I don't want to go back to using Windows.

I've installed 11.10 using wubi next to a Windows 7 Home Premium.

---

### Post by Rubi1200 on 2011-11-07
Hi,
I have moved your post into its own thread where it is likely to get more attention.

Thanks for understanding.

---

### Post by Mark Phelps on 2011-11-07
Don't understand -- if you're trying to get away from Windows, then why install using Wubi (INSIDE Windows) and why mount NTFS volumes?

The CPU usage is most probably due to the combination of Wubi and NTFS mounting.

If you REALLY want to get away from MS Windows then you should be running Ubuntu in its own partition.  You shouldn't then be encountering NTFS mounting problems that way.

---

### Post by stfnmchr on 2011-11-11
You're right, I did not explain myself fully. I need Windows for some tasks, like working from home etc, but on a daily basis I want to use Ubuntu. 

So you are saying that I should have on my HDD a NTFS partition for Windows and a Ext4 one for Ubuntu? So I would need to remove ubuntu and repartition my hdd?

---

