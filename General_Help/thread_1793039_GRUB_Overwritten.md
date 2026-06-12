---
title: "GRUB Overwritten"
date: 2011-06-28
forum: General Help
---

### Post by hello cruel world on 2011-06-28
I recently created a triple-boot netbook. I have latest Ubuntu, BackTrax 5, and Windows 7 on it. I had it working fine. When I tried to follow a Truecrypt tutorial on getting windows partition encrypted I ended up overwriting the MBR(ie: GRUB). Now I knew this would happen, but what I didn't expect was that the Truecrypt Boot loader wouldn't detect a bootable partition. 

The windows 7 partition hadn't been encrypted, yet. True crypt was just doing the test feature, before drive was encrypted. So I believe my Linux partitions and very well my windows 7 partitions are still in-tact. However, I can not get the partitions to load, due to Truecrypt loader not working.

I have tried SuperGrub2, which didn't detect partitions, and Rescatux, which did detect partitions but failed every time. I was trying to follow a grub re-install ([https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)) via command line, but ran into some hiccups along the way. 

If anyone can walk me through the process of reinstating GRUB I will very thankful, and if requires a lot of your time I can reimburse you through Paypal. I have never had to seek help for these kind of issues, before. I am new to Linux, so that has severely hampered my progress so far.

---

### Post by andrewthomas on 2011-06-28
You probably have grub2 and those instructions are for grub-legacy.

Use these instructions:

[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by hello cruel world on 2011-06-29
Thank you very much. Ubuntu Secured was a lifesaver! Boot Repair worked much better than the other techniques.

---

### Post by andrewthomas on 2011-06-29
You're welcome.

Glad to be of help.

---

