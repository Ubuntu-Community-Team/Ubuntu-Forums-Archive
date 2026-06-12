---
title: "Power management problems in 12.04"
date: 2012-05-29
forum: General Help
---

### Post by Helios747 on 2012-05-29
Hello,


I'm running Ubuntu 12.04 x64 with the latest updates on my ASUS K53E.

After a vanilla install of any ubuntu version, the K53E will not suspend properly. A script from here ([http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)) fixes it right up.

However, for the past few days I've been getting more severe PM problems. The system will lock up when rebooting, shutting down, suspending. It will start the process of shutting down/suspending, but then it will just go to a black screen. System and LCD still on, but a black unresponsive screen. Behavior identical to how suspend behaved before installing that suspend script.


The very odd thing, is that this problem is seemingly random. Sometimes the laptop will suspend/shut down just fine. Sometimes it will lock up, making it difficult to tell whats causing this problem or how to fix it.

Is there a log somewhere I can post to help give a better idea of what's going on?

Thanks.

---

### Post by Helios747 on 2012-05-29
Bump. I really need help with this.


The laptop doesn't want to shutdown/reboot/suspend at all now.

---

### Post by Helios747 on 2012-05-29
Bump. Tried reinstalling. Fresh install the laptop wouldn't shutdown or suspend. Normal.

Installing any one of 3 ehci fixing scripts will let the laptop suspend once, but trying to do it again it will simply lock up.

Kernel 3.4 advertised some fixes to USB and suspending. Trying that kernel, again. Laptop would sleep once, but lock up and crash if attempted again.

The frustrating thing is that this script always worked in earlier versions of Ubuntu, and in other Linuxes, like Mint 12 and Fedora.

Help!

---

### Post by Helios747 on 2012-05-30
Fedora had their newest release today, Fedora 17.

I gave it a spin with the LiveCD. Suspend worked OotB and honestly that's a really important feature for me. That and battery life, which appears to be about the same, so I'm switching to Fedora.


Here is a link to the script I was using in Ubuntu for anybody stumbling across this thread. It worked in 10.04, 11.10, and stopped working in 12.04.

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)


Here is another script that does more or less the same thing in a different way.

[http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822)

6th reply by John Dias.

---

### Post by 2F4U on 2012-05-30
Since you don't provide any info about your hardware and relevant info from the log files, its unlikely that someone will be able to help diagnosing the problem. But I guess it doesn't matter since you switched distributions. So good luck with Fedora.

---

### Post by Helios747 on 2012-05-30
I didn't know where I could find relevant log files, I asked which log files would be relevant in the OP as well.

---

### Post by 2F4U on 2012-05-30
For debugging suspend/resume issues, /var/log/pm-suspend.log is a valuable resource as well as /var/log/syslog. You may have to use sudo to be able to view the files.

---

### Post by Helios747 on 2012-05-30
Thanks for the information. I'll keep that in mind next time. :)

---

