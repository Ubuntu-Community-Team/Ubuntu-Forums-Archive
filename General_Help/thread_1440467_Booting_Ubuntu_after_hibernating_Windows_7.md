---
title: "Booting Ubuntu after hibernating Windows 7"
date: 2010-03-27
forum: General Help
---

### Post by locombian on 2010-03-27
Hello,

I recently made the mistake of booting Ubuntu after hibernating windows 7. Now I can't boot windows or the recovery mode, 

Any suggestions,

Thanks

---

### Post by Muscovy on 2010-03-27
Hold ESC (escape) while booting up your computer. Grub, the program that lists boot options, might be set with a display time of 0.

---

### Post by dcstar on 2010-03-27
> **locombian said:**
> Hello,

I recently made the mistake of booting Ubuntu after hibernating windows 7. Now I can't boot windows or the recovery mode, 


Having another program access a hibernated OS partition usually results in disaster.

You need to find a Windows repair disk/solution somewhere if your Windows system won't boot, you probably won't find it in a Linux forum.

---

### Post by Mark Phelps on 2010-03-27
It's a bad idea to use hibernation if you (1) have different OSs installed and (2) don't keep track of what OS you were in last.

When you were in Win7, did you take the trouble to use the Backup facility to create and burn a Win7 Repair CD?

If you HAD, you would be able to boot from that now and run Startup Repair to fix your Win7 boot problem.

If you do NOT have such a CD, goto the link below, read the instructions, download the proper disk image, burn it to CD, and then boot from it to repair Win7:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

