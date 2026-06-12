---
title: "Windows can'boot after linux kernel upgrade"
date: 2010-12-02
forum: General Help
---

### Post by Colossus121 on 2010-12-02
I updated ubuntu and installed the latest linux kernel. I rebooted back into ubuntu, then finished up some work and went to reboot into windows 7. The "starting windows" logo comes up then it blue screens and says "cannot boot %hs missing" (hard to read because it flashed on the screen then reboots).

I ran startup recovery but that didnt do anything. I also tried downgrading the kernel but that didnt change anything.

Please help.

---

### Post by Rodney9 on 2010-12-02
Insert and boot from your WindowsXP CD. 
At the first R=Repair option, press the R key 
Press the number that corresponds to the correct location for the installation of Windows you want to repair. 
Typically this will be #1 
Type bootcfg /list to show the current entries in the BOOT.INI file 
Type bootcfg /rebuild to repair it 
Take out the CD ROM and type exit

I hope it works out for you

---

### Post by Colossus121 on 2010-12-02
I dont have a cd drive or an install disc i can get for a few days.

(also i have windows 7 not XP) 

Any idea why updating the kernel would cause this?

---

### Post by Colossus121 on 2010-12-02
Found out what the problem was.

Before I shut down windows, AVG updated and needed me to reboot. Due to an error in the latest update, AVG screws with the boot sequence and as a result blue screens windows. I found out all i had to do was browse around Program files on my windows partition and rename the avg folder. After doing so windows booted without a problem.

---

### Post by cmoman on 2010-12-02
AVG has hosed a number of 64bit Windows 7 machine at our work.  The problem is caused by AVG updating a disk driver - they forgot to include a 64bit disk driver.
AVG are now aware of the problem and will no doubt fix the update.  In the meantime, best to keep your computer on if running 64bit Windows 7 and not reboot.
If you are now experiencing the problem, you can use a system restore point to roll back the changes after booting into Safe mode.
If you don't have the system restore point option, you may need to put the affected disk into another computer to copy the missing file across.  Multi OS users may have other options.

The issue isn't related to Linux, rather AVG and Windows 7 64bit. Other Windows 64bit systems may be affected but all our Vista machines are 32bit so I don't know the scope.

This is sure going to cause some constenation amongst non technical users with on one Windows 7 64bit machine at home who have hit the 'Reboot Now' option after the AVG update.

---

### Post by Colossus121 on 2010-12-02
I was able to fix the problem and have replaced AVG with the official windows antivirus software, which I actually like more than AVG.

---

### Post by Colossus121 on 2010-12-02
double post removed

---

