---
title: "Adding Windows 7 to system with Ubuntu 12 on it"
date: 2012-09-07
forum: General Help
---

### Post by Julian1968 on 2012-09-07
Hello

I have Ubuntu 12 installed but want to add Windows 7 without taking Ubuntu off first.

I cant find any guides for this and wonder if you guys can help me out please?

Thanks

---

### Post by Epodx64 on 2012-09-07
Is there any chance you could add Windows 7 to a different HDD? If you can you can just select which hdd to boot first in the bios.

---

### Post by Julian1968 on 2012-09-07
> **Epodx64 said:**
> Is there any chance you could add Windows 7 to a different HDD? If you can you can just select which hdd to boot first in the bios.

No. I have the one hardrive on my laptop so Im thinking I have to split it

---

### Post by Epodx64 on 2012-09-07
hmm... I'm honestly not sure I know how to do it if Windows is installed first but I think a fresh windows install will wipe out grub... accutally that might be alright just install windows normal just make sure you setup a partition for it with GParted then install windows on that partition then run the Ubuntu LiveCD and go thru the install process all over again just don't format anything and just install grub that should do it.

---

### Post by Julian1968 on 2012-09-07
> **Epodx64 said:**
> hmm... I'm honestly not sure I know how to do it if Windows is installed first but I think a fresh windows install will wipe out grub... accutally that might be alright just install windows normal just make sure you setup a partition for it with GParted then install windows on that partition then run the Ubuntu LiveCD and go thru the install process all over again just don't format anything and just install grub that should do it.

I guess I could just go for a fresh instal of both. Thanks

---

### Post by krustenBrot on 2012-09-07
If you are doing a fresh install remember to **first** install Win7 and then Ubuntu. That way it is a lot easier. If you are trying to keep your Ubuntu Install *Grub* will be overriden by Windows So you will have to fix that in order to boot up Ubuntu. Plus: Splitting your Partition might be more comfortable using gparted on Ubuntu. As far as i know the comparable Windows tools are not that great. Good luck! :)

---

### Post by Julian1968 on 2012-09-07
> **krustenBrot said:**
> If you are doing a fresh install remember to **first** install Win7 and then Ubuntu. That way it is a lot easier. If you are trying to keep your Ubuntu Install *Grub* will be overriden by Windows So you will have to fix that in order to boot up Ubuntu. Plus: Splitting your Partition might be more comfortable using gparted on Ubuntu. As far as i know the comparable Windows tools are not that great. Good luck! :)

Yeah, I was thinking, from the info and help on the net that the Windows first option would be best

Thanks again

---

### Post by mastablasta on 2012-09-07
you can crete empty disk space (or NTFS formated) and install  windows to it. you need a primary partition for that. then after install is finished Grub will be overwriten, so you need to "repair it" (you can use boot repair tool for that).

---

### Post by Cheesemill on 2012-09-07
Have you read the wiki?

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

