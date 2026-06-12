---
title: "I can't enter last Ubuntu 11/10 through Windows wubi"
date: 2012-03-22
forum: General Help
---

### Post by Jayhawker on 2012-03-22
Mine is Linux Ubuntu 11/10 through Windows' wubi. After a forced shutdown because all windows got stuck, I've tried to enter again, but screen doesn't get into Linux. In remains lilac, before the opening of the little window on the left asking for the password.  

How to reenter in Ubuntu? 

Thanks a lot

---

### Post by Karlchen on 2012-03-22
Hello, Jayhawker.

> Mine is Linux Ubuntu 11/10 through Windows' wubi. After a forced shutdown because all windows got stuck, I've tried to enter again, but screen doesn't get into Linux. In remains lilac, before the opening of the little window on the left asking for the password.  
The term "forced shutdown" suggests that you simply switched off the machine by pressing the power button for 5 seconds or more.
In this case it is not totally unlikely that the Ubuntu filesystem has been damaged, and/or that the underlying Windows filesystem needs some checking.
So I suggest you boot the machine in normal Windows mode. Then you launch the command prompt in elevated mode and tell Windows to perform a chkdsk of the partition which holds the folder \ubuntu. 
Let us assume that you have installed Ubuntu on the Windows partition D:, the commandline to enter at the elevated command prompt would be ```
fsutil dirty set D:
``` Windows will tell you that drive D: has been marked "dirty".
Close the command prompt and reboot Windows.
Prior to the normal boot Windows will start performing a chkdsk on drive D:. Do not interrupt it.
Once Windows has finished the chkdsk and the normal boot, reboot Windows again.
This time inside the boot menu select Ubuntu and try whether Ubuntu will boot normally again.
In case the Ubuntu boot process does not finish again you will have to perform an fsck on the Ubuntu file system which is located inside D:\ubuntu\disks\root.disk, provided you installed Ubuntu on Windows partition named drive D:.
A concise instruction how to perform an fsck of the root.disk can be found here: [Section titled **How can I access my Wubi install and repair my install if it won't boot?**]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?")

Kind regards,
Karl

---

