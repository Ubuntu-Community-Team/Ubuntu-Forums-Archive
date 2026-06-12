---
title: "How to use fake Raid 1 array - Intel chipset"
date: 2009-08-03
forum: General Help
---

### Post by billmilosz on 2009-08-03
How do I mount Raid 1 drive pairs that I created in Windows?

INFO:

1. Dual boot system - XP64 and Ubuntu 9.04 64 x86 desktop working OK.  Boot / System drive NOT RAID

2. Pair of SATA drives configured as Intel RAID 1 under Windows to store data in mirrored drives for safety.  They show up under Ubuntu as two seperate disks.

3. I tried installing DMRAID  but Ubuntu told me files were locked....

NOTE: **I DO NOT need to boot off raid**- only to mirror two drives where data is being stored.

---

### Post by haider_up32 on 2009-08-16
i have the same problem

---

### Post by billmilosz on 2009-11-01
Wow, great support here for Ubuntu.  Really makes me feel like using it.....  NOT.

---

### Post by Monotoko on 2009-11-01
Billmilosz - The people on this forum who help are all volunteers, you are not entitled to help, but people still help when they can. We learn from experiance, we are not Microsoft Techie's given a script.

As for your question, i do not know, i have never used RAID, you will need to wait for someone who has...If they are still willing to help you after your comment.

---

### Post by Kokopelli on 2009-11-01
can you be more specific on "3. I tried installing DMRAID but Ubuntu told me files were locked...."?

---

### Post by seamuso on 2009-11-01
how are you installing dmraid? from a terminal? do you have synaptic open at the same time?

if you're installing from a terminal, are you making sure to sudo?

How did you create the raid set? With the bios utility or with software inside of windows? If you created it in windows, when the computer boots, do you have an option to get into a raid bios during system start up?

4 of the 6 drives in my signature for my desktop system are a raid5 setup. I have an nvidia fakeraid, but the setup should be the same.

If you did install dmraid already, make sure you reboot and check /dev/mapper what do you have in there?

---

