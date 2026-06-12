---
title: "Remove win7"
date: 2011-11-20
forum: General Help
---

### Post by Brizlitman on 2011-11-20
How do i safely remove the win 7 partition from my dual boot setup. i now have a win7 vm so i no longer need to dual boot.

---

### Post by Kelvari on 2011-11-20
If you're looking to fully remove Windows 7 from your laptop, and did NOT install Ubuntu through WUBI (WUBI only installs it as a program in your Windows partition), you should be able to run GParted from a LiveCD/LiveUSB and use that to remove your Windows partition(s). Once that has been taken care of, you can move and/or re-size your partitions as desired. Be warned, though, that moving and resizing partitions can take quite some time, so it is best to do so while your laptop is plugged in.

---

### Post by tartalo on 2011-11-20
Afer removing the partition:
```
sudo update-grub
```

---

### Post by raja.genupula on 2011-11-20
> **Brizlitman said:**
> How do i safely remove the win 7 partition from my dual boot setup. i now have a win7 vm so i no longer need to dual boot.

IF you installed Ubuntu on a separate partition then 
1...boot into Ubuntu
2...open Disk utility
3...format the Win7 installed drive
4...open your terminal
5...sudo update-grub

Thats all and everything will be fine..
Before doing format dont forget to take out IMP data backup in your windows drive , if you have .

all the best.

---

### Post by Brizlitman on 2011-11-20
Is it really that easy?

---

### Post by elliotn on 2011-11-20
> **Brizlitman said:**
> Is it really that easy?

yes it is...and mark as solved

---

### Post by Latulipe on 2011-11-20
And what when I DID install Ubuntu through WUBI ?

---

### Post by elliotn on 2011-11-20
> **Latulipe said:**
> And what when I DID install Ubuntu through WUBI ?

its either u do a clean install or try to move your wubi to a partition

---

### Post by Latulipe on 2011-11-20
Tnx elliotn.

I just found this HowTo : [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) . Is that the way to do it ?

Is one of the two ways ( clean install or move) the best way to get only 11.10 without W7 ?

---

### Post by raja.genupula on 2011-11-21
I support clean install for risk free use and better performance, Take any IMP backup before that. 
All the best.

---

