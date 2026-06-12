---
title: "Ubuntu 11.10 freezes during boot"
date: 2011-10-17
forum: General Help
---

### Post by goehle on 2011-10-17
After my upgrade to 11.10 I can't get my machine to work.  

1.  If I try to boot normally it freezes at a black screen with a cursor. 

2.  If I try to boot in recovery mode it gets to "rtc_cmos 00:05: setting system clock to ..." and freezes. 

3.  I can start up under an older kernel (anything other than kernel 3) but then I can't get graphics to work properly. 

Any suggestions?  Its definitely a kernel issue because I can at least get to a command line with another kernel.  Its pretty low level because when the computer freezes during the recovery boot up I can't even use the SysRq commands.

---

### Post by guyfromfl on 2011-10-17
I'm now having a similar issue.

Before, I lost internet, but had networking.

Now, When I try to boot, I get stuck on the Ubuntu screen with the 5 dots.  Recovery mode doesn't do much it gets caught trying to mount my NAS drive.

This upgrade has been the most frustrating yet, not to mention I get to look forward to trying to replace Unity after I get it up and running...

Day 3 of work going down the drain.

---

### Post by @ether on 2011-10-18
Similar problem.  freezes during boot after clean install 11.10 (desktop 32 bit).  11.04 is installed alongside, bootes without a problem (running kernel version 2.6.38-11)
Oh well, still great value for money ;)

---

### Post by BoneXXX on 2011-10-19
I am having the same problem  as well, any help ?

---

### Post by dabatla on 2011-10-19
I had a similar problem, I found my solution in the following bug request.

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/858122](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/858122)

---

### Post by BoneXXX on 2011-10-19
And I found my solution at here: [http://askubuntu.com/questions/68220/ubuntu-11-10-wont-boot-with-nvidia-driver-enabled](http://askubuntu.com/questions/68220/ubuntu-11-10-wont-boot-with-nvidia-driver-enabled)

I hope these solutions will help to others, cause took me so long to fix this issue for me.

---

