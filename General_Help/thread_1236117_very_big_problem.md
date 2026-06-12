---
title: "very big problem"
date: 2009-08-09
forum: General Help
---

### Post by audiologic on 2009-08-09
I installed ubuntu 9.04 on a gateway m-6888u laptop, running windows vista 64 bit. Ubuntu was running phenomenal. However, when starting my computer, I was give TWO windows vista options. They both said windows vista loader, or something like that. I selected the first one. The gateway system recovery came up. So I selected restore factory defaults, as the other option was "exit". This restored my computer to the orgiinal vista settings. Ubuntu is still an option, but there's four to choose from: One says generic build 9.04, then a 14 after it; the other says the same, but recovery mode. Then there's two below that are the same, one recovery and one normal, but there's an 11. When I try to run UBuntu it freezes.

Basically, I restored my system and it messed my ubuntu up. What should I do?

---

### Post by zkriesse on 2009-08-09
At this point you could try sticking int your Ubuntu cd and either try the repair system option or you could re-load the system...

---

### Post by merlinus on 2009-08-10
Whilst running from the live cd, open a terminal and post results of

```
sudo fdisk -l
```

to see if the vista restore wiped out ubuntu.

---

### Post by cariboo on 2009-08-10
HAve a look at this [howto]("http://ubuntuforums.org/showthread.php?t=224351") I have used it several times to fix grub problems.

---

### Post by zkriesse on 2009-08-10
I agree with Cariboo

---

### Post by audiologic on 2009-08-10
tried re-installing the system. that caused more problems.

any way to scratch it all and start from the beginning? now i'm left with like a million boot options, one gets into UBUNTU but none of the packages are working and there are errors left and right, and the other one still freezes and flickers and such, I just want to repartition everything to windows and start over.

---

