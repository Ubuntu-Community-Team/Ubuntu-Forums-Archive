---
title: "System freezes"
date: 2012-02-24
forum: General Help
---

### Post by Fahrbot on 2012-02-24
Hi, I'm having problem with my newly installed HTPC which is running Ubuntu Server 11.10 32-bit. The system is overall stable and I haven't experienced any random crashes or freezes.

But I have one **major** problem, if I do a SFV-check on several SFV-files the system completely freezes. The system stops responding to ping, can't access the terminal, can't enable/disable caps lock on the keyboard etc etc. It doesn't matter if I use rhash or cfv when I'm running the SFV-checks the system freezes up anyways. At first I thought that maybe it was the CPU overheating so installed lm-sensors and kept a eye on my CPU while running the SFV-checks, but I never got over 40°C before the system crashed.

So just to clarify I check several SFV-files using this command and my system crashes big time and I have to reboot using the power button.
```
fahrbot@Zoidberg:/media/raid/movies$ cfv -r
```Any ideas anyone? :cry:

**Hardware**
CPU: Intel Core i3 2100
Motherboard: Asus P8H67-I B3
RAM: Corsair XMS3 8GB

---

### Post by idonthaverabbies on 2012-02-24
have you tryied memtest ?i have issues with ubuntu to going to try mint linux . im sure ubuntu is a decent os but its not good on my rig

---

### Post by Fahrbot on 2012-02-24
Did a quick memtest with two passes and no errors. So it doesn't seem to be the RAM either.

---

### Post by Fahrbot on 2012-02-24
If I perform the SFV-checks manually by doing one check at the time it works fine.  :???:

---

