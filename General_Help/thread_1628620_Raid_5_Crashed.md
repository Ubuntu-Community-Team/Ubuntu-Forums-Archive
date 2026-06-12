---
title: "Raid 5 Crashed"
date: 2010-11-22
forum: General Help
---

### Post by ShadowcatX on 2010-11-22
I'm a casual Ubuntu user and even more casual forum guy, but I've ran into a brick wall and I need some help. I've done a search for crashed raid on these forums and didn't come up with anything. 

I set up a software RAID 5 on Ubuntu Server at work several months back. The server has a boot disk and 4 other disks that run as the RAID. It was running fine so I just left it alone. Today, suddenly no one was able to access their files so I went to have a look and the hard drive light was not on on the tower. I restarted my tower and got a message that 194 updates needed to be installed. I installed them and restarted. 

When I got back on and went to mount the raid, I saw that it has a problem. In disk editor I see 5 sections on the disk. 3 of them have free space and 2 are "unknown". Both of the unknown sections are "poorly aligned" and may cause poor functionality. This was not how it was when the RAID was running. 

Does anyone have any suggestions on how to fix the RAID without loosing my department's data? I was thinking I might use the disk editor to check and repair the RAID, but I wanted to double check that it won't loose my department's data. 

If you need any more information, I'll do my best to get it for you. Thank you in advance for your help.

---

### Post by t4thfavor on 2010-11-22
Make an offline backup, before you touch anything!

Other than that, I'm not sure. I never got RAID on Linux working on anything but higher end servers with "real" RAID arrays.

If you have a "real" raid controller, the fixing should be done in the raid utility during boot, if it's softraid, then I'm out of help.

---

### Post by ShadowcatX on 2010-11-23
I'm not sure I'm going to be able to make an offline backup. We have around 1 terrabyte of data and nothing else that can hold that much. Its a good idea though and I will look into it. Any suggestions on how to go about it, assuming I find something that will work?

---

### Post by searchfgold6789 on 2010-11-23
Clonezilla will do that part for you (the backing up)

---

