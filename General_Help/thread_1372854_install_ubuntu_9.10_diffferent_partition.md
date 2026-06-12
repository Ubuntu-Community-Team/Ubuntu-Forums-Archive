---
title: "install ubuntu 9.10 diffferent partition"
date: 2010-01-05
forum: General Help
---

### Post by andy1983 on 2010-01-05
I have win xp and win 7 on two diff. partitions. Now I want to install ubuntu 9.10 on diff drive of 30 GB. But I dont want grub to take charge of win 7 boot loader. I want there should be entry of Ubuntu 9.10 in win 7 bootloader in the end.

How to do it?

---

### Post by jamesisin on 2010-01-05
I think the preferred method is to install grub and then run a repair from the Windows installer to fix the Windows boot loader.  A little searching on the forums will yield a lot of information on this.

---

### Post by andy1983 on 2010-01-05
I am not used to with repair utilities. 3 days before I had installed ubuntu 9.10 and it screwed me and my laptop. Thanks for this forum and the experts who help me to make my system accessible. That is why I want to know is there any way so I can install 9.10 on different partition and it should not capture bootloader.

---

### Post by dcstar on 2010-01-05
> **andy1983 said:**
> I have win xp and win 7 on two diff. partitions. Now I want to install ubuntu 9.10 on diff drive of 30 GB. But I dont want grub to take charge of win 7 boot loader. I want there should be entry of Ubuntu 9.10 in win 7 bootloader in the end.

How to do it?

You select the Advanced Options during the install process and specify which partition has Grub installed.

---

### Post by andy1983 on 2010-01-05
Thanks for reply. Which partition should I use after going in to advance option so I can have ubuntu entry in win bootloader ?

---

### Post by Leppie on 2010-01-05
if you install ubuntu on a seperate disk and set that disk as the 1st boot drive, you can still use grub as the bootloader without changing anything to your windows disk (hence, removing the ubuntu disk from the machine would leave you with a completely functional windows system).

---

### Post by andy1983 on 2010-01-05
Hi again Leppie,

Thanks again for your help but i already solved it. First I installed ubuntu on desired drive and installed grubloader on the root partition which did not overwrite MBR. Then using Easybcd 2 I add grub2 entry in MBR. This solved my question.

Thanks a lot all of you and this forum for sharing your knowledge with me.=D>=D>=D>=D>=D>

---

