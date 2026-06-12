---
title: "After Latest Update, Unable to Suspend"
date: 2011-01-28
forum: General Help
---

### Post by MSwal2846 on 2011-01-28
Team,

I'm running 10.10 on a Lenovo x200.  I have been running, happily, with 10.10.  Yesterday, the update manager installed:

[PHP]Start-Date: 2011-01-27  06:42:20
Install: linux-headers-2.6.35-25:i386 (2.6.35-25.44), linux-headers-2.6.35-25-generic-pae:i386 (2.6.35-25.44), linux-image-2.6.35-25-generic-pae:i386 (2.6.35-25.44)
Upgrade: icedtea6-plugin:i386 (6b20-1.9.2-0ubuntu2, 6b20-1.9.4-0ubuntu1), linux-image-generic-pae:i386 (2.6.35.24.28, 2.6.35.25.32), icedtea-6-jre-cacao:i386 (6b20-1.9.2-0ubuntu2, 6b20-1.9.4-0ubuntu1), linux-libc-dev:i386 (2.6.35-1024.42, 2.6.35-1025.44), openjdk-6-jre-headless:i386 (6b20-1.9.2-0ubuntu2, 6b20-1.9.4-0ubuntu1), openjdk-6-jre:i386 (6b20-1.9.2-0ubuntu2, 6b20-1.9.4-0ubuntu1), openjdk-6-jre-lib:i386 (6b20-1.9.2-0ubuntu2, 6b20-1.9.4-0ubuntu1), linux-generic-pae:i386 (2.6.35.24.28, 2.6.35.25.32), linux-headers-generic-pae:i386 (2.6.35.24.28, 2.6.35.25.32)
End-Date: 2011-01-27  06:44:18[/PHP]

After this update I am unable to Suspend.  The screen goes black, the harddisk spins, the moon blinks a couple of time and then I'm presented with the Lock Screen.  

I have:

[LIST]
[*]Kernel Linux 2.6.35-25-generic-pae
[*]3.6 Gib of Memory
[*]Availabe disk space of 75.6 GB
[/LIST]

Let me know what additional information is required to help fix this.  Thank you!

---

### Post by mrhhug on 2011-01-28
suspend problems usually has to do with graphics drivers. 

your using a Integrated Intel X4500 HD and intel drivers should just work cause they are opensource

[https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html](https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html)

if that doesnt work go here: [https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance)

---

### Post by TheJackal12 on 2011-01-28
I own a x200t and my suspend was also broken after the latest updates. :\ Everything was going so smoothly!

---

### Post by MSwal2846 on 2011-01-29
Thanks mrhhug, but neither of those links worked for me.  The script link didn't exist, I found the script however, it said everything was ok.  Also, this link seemed to imply that the problem was my Intel graphics card, BUT it was working BEFORE the update ... so the problem is in the UPDATE (since it is what changed) and not my graphics.

How does one alert Ubuntu on this?

---

### Post by philinux on 2011-01-29
> **MSwal2846 said:**
> Thanks mrhhug, but neither of those links worked for me.  The script link didn't exist, I found the script however, it said everything was ok.  Also, this link seemed to imply that the problem was my Intel graphics card, BUT it was working BEFORE the update ... so the problem is in the UPDATE (since it is what changed) and not my graphics.

How does one alert Ubuntu on this?

From grub menu try the previous kernel and see if suspend works. If it does then it's the new kernel.

Boot normally then run in a terminal.

```
ubuntu-bug linux
```

You'll need to have registered at launchpad to report the bug for your hardware.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by MSwal2846 on 2011-01-29
There is actually a bug out there that aligns pretty close to my issue:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625364?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625364?comments=all)

In the dialog with that ticket, there was a suggestion to try:

    sudo rmmod tpm_tis && sudo modprobe tpm_tis itpm=1

Which actually did the trick, for now...

---

### Post by TheJackal12 on 2011-01-29
Sweet. That worked for me too :D.

---

### Post by adb3 on 2011-02-11
I had exactly the same problem on my X200. Blacklisting tpm_tis worked for me. Let's hope for a real bugfix soon!

Thanks!!1

---

