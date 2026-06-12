---
title: "setting up extra drives 9.10"
date: 2009-11-10
forum: General Help
---

### Post by technicallygeek on 2009-11-10
I have three extra 80gig drives that I want to use as extra space I guess... 

I can get them formatted but when I reboot the system. the computer wont boot. it's like it's trying to boot from the dirve that doesn't have GRUB installed on it or read the /boot, or / 

How can I get these extra drives set up so that when I shut the computer down it wont try to read them and boot from them. I set the boot order via the bios and it still didn't work

---

### Post by sklyer on 2009-11-10
Can you boot into your system if the drives are not physically connected? (Just to be sure that Grub is working correctly and is where you think it is.)

---

### Post by technicallygeek on 2009-11-10
yea if I disconnect the drives then the system boots just fine.

---

### Post by technicallygeek on 2009-11-10
okay on a whim cause at this point im testing to see what the problem is. I formated one of the drives with a partition of mbr and FAT rebooted and where grub would usually kick I got a flashing cursor. I went into the boot order via F11 and in the order I have the IDE disk with the user home directory listed first then the sata drive I just formatted to FAT listed second and the SATA drive with the swap, /boot, and / listed as the last drive. 

I have set in the bios that the SATA drive with swap,/boot,/ to be the first boot device. It is also connected as SATA1 on the board

I have been trying to get these three SATA drives setup as just extra space for like three days now and have not been able to get my machine to see them that way it always wants to boot to them.

---

### Post by technicallygeek on 2009-11-10
I think I fixed the problem, some how my bios keeps trying to change the boot order. Now I have a raid5 set up on the drives

---

