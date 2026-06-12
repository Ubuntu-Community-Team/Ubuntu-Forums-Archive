---
title: "Hardware Error while booting"
date: 2011-12-18
forum: General Help
---

### Post by eleks on 2011-12-18
Hello,

for a couple of days I am getting system freezes both after logging into Ubuntu and Windows, but I had no idea what caused them. Now, finally I was presented this bootlog in my "screenshot".

So it seems obvious that my CPU was causing the freezes, my question is now simply: Could it also be caused by the mainboard or is it definitely the CPU? (I.e. if I buy a new CPU and replace it, will the problem be solved or do I need to do further checks?)

(It's not really a Ubuntu question but I am sure you are the best audience to pose it to)
Thank you very much!

Patrick

---

### Post by LinuxFan999 on 2011-12-18
You are getting a kernel panic, which is very bad, and can indicate faulty hardware.
 
If you have another CPU available, or if you buy another one, remove the origional CPU, and insert the other one, then try booting up. If it boots up succesfully after switching the CPU, then the origional CPU has gone bad. If the error still occurs after switching the CPU, the motherboard is the cause.

---

### Post by 2F4U on 2011-12-18
Take into consideration that it may be difficult to replace the old CPU without damaging the mainboard. The CPU will be attached to the mainboard using a cooling paste. It will be required to use some force to remove it, which may damage the mainboard. So it may be a good idea to also get a new mainboard.

---

### Post by eleks on 2011-12-18
Thanks for the help!

First I'll try to replace the CPU, if that does not work/help I'll buy a new mainboard as well.

---

### Post by bluexrider on 2011-12-18
> **eleks said:**
> Thanks for the help!

First I'll try to replace the CPU, if that does not work/help I'll buy a new mainboard as well.
depending on the age of the MB and CPU combo it might be relevent to just replace them both.

ATX mainboards are fairly cheap and last years processors are too.

---

### Post by eleks on 2011-12-26
Just a quick update: Replaced the CPU and still not booting. Trying the mainboard next...

---

### Post by eleks on 2012-01-05
Turns out it was the mainboard. Replaced it and everything is working again.

---

