---
title: "Prob when installing Ubuntu"
date: 2006-03-05
forum: General Help
---

### Post by ubuntu_probs on 2006-03-05
Today I tried to install ubuntu in the same disc of windows, in anoher partition, everything correct. But my surprise went when, the program was ready to make the ext3 partition and the swap partition, everything was fine, and then an error appeared:

```
Input/output error during read on
/dev/ide/host0/bus0/target0/lun0/disc

ERROR!!!

-Retry
-Ignore
-Cancel
```

I rebooted the system as soon and I could, I tried to enter windows and.. there was no windows, even, there was no boot anywhere, so i tried to install ubuntu again and all the partitions on the C: disc were deleted.. well, strange . but the prob is, I cant try to make a partition on this disc now: on linux partition program it says the same error that before, and in windows it says that it can't have access to that disc... But its still detected by both OS...

What I have to do now? everything was correct.. need help fast please :(, ty.

---

### Post by az on 2006-03-05
[QUOTE=ubuntu_probs] so i tried to install ubuntu again and all the partitions on the C: disc were deleted.. well, strange . but the prob is, I cant try to make a partition on this disc now: on linux partition program it says the same error that before, and in windows it says that it can't have access to that disc... But its still detected by both OS...

What I have to do now? everything was correct.. need help fast please :(, ty.[/QUOTE]


What happens if you boot the installer, let it detect your hardware and load the components and then go to the shell (CTRL-ALT-F2) and run
parted
print

do you see any partitions?

If not, try rescue (in parted)
rescue
0
(type in the size of your old partition)  
It will scan tat area and try to detect a former partitoin there.  If it finds one, it will ask you if you want to add it to the partition table.  Say yes and reboot.

---

### Post by ubuntu_probs on 2006-03-05
Damn, I'm new to this and didn't even understand a word of that you say, could you repeat it more extensed? I'm new to the partitions and linux things :( ,ty :p

Btw, I have another HD of 120gb that I DON'T WANT TO TOUCH....

---

### Post by ubuntu_probs on 2006-03-05
hey please answer me I really need help, can't do that rescue thing

---

### Post by ubuntu_probs on 2006-03-05
Bump... I NEED HELP, doesnt anyone know???

---

### Post by ubuntu_probs on 2006-03-05
bump..what a help..

---

