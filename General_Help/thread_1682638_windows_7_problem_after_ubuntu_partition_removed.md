---
title: "windows 7 problem after ubuntu partition removed"
date: 2011-02-06
forum: General Help
---

### Post by alababi on 2011-02-06
Windows 7 crashed yesterday and I decided to reinstall it from the recovery partition which is preinstalled in my laptop. The only option avaiable was to restore the hard drive into the default setup ( with only one partition ( besides the recovery one) and windows 7).

However, after the reinstalling process ran up about 80%, an error appeared showing that:
```
 error: no such partition.
grub rescue >
```

Then I used a ubuntu CD to boot and saw that all partitions were deleted ( including the /root, /home ... of linux). I restarted the laptop to reinstall again but faced the error again.

What should I do now? I never encountered this error.

---

### Post by oldfred on 2011-02-06
You are using a windows restore. But you still have grub installed to the MBR. You also need to have windows boot loader in the MBR. 

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

BootRec.exe /fixMBR

---

