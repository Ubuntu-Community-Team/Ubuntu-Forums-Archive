---
title: "Reformat hard drive from linux to fat 32 or NTSF"
date: 2012-03-18
forum: General Help
---

### Post by chicoharv on 2012-03-18
I have a wife that has had a stroke and cannot operate her laptop with ubuntu  and xp both installed. She only uses it for games. I need to take Ubuntu off and reinstall only windows. My PC beginner disc will not work as it was made for Fat 32. How can I reformat my hard drive and restore the original XP which I have the CD's for but I must get rid of the linux partitions and grub to do this

---

### Post by 2F4U on 2012-03-18
Do you have a liveCD of Ubuntu? If yes, you can boot it and use the partitioning tool to delete all partitions. Then shutdown the computer and start with the Windows installation cd. Windows will then override the MBR with its own bootloader and therefore eliminate grub.

---

### Post by chicoharv on 2012-03-18
Thank you, worked great.:p

---

