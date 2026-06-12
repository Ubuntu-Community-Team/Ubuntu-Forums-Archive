---
title: "Asus 1201N Netbook won't wake up from suspend"
date: 2012-09-15
forum: General Help
---

### Post by Spamicles on 2012-09-15
My Asus 1201n won't suspend properly (screen goes dark but power button remains solid instead of blinking). I have to cycle power to get it come back on. I only found old solutions from previous Ubuntu versions which included updating to a more current kernel (now an older kernel). Is there anything I can try to fix this? I'm new to Ubuntu so let me know what sort of diagnostic info I should post. I recently updated to the most recent version of my BIOS from Asus but this didn't fix the problem. Thank you!

---

### Post by Spamicles on 2012-09-15
Fixed this (and related problem that computer would not suspend on command pm-suspend). Did sudo gedit /proc/acpi/wakeup . Had to disable everything in this file (USB0, USB2, and some other things were enabled) by doing sudo echo <thing> > /proc/acpi/wakeup where <thing> is USB0, USB2, and other things in the column of this file. I believe this tells the computer what can and cannot wake the computer.

---

### Post by SeijiSensei on 2012-09-16
Anything under /proc will not survive a full reboot.  It's a filesystem that the kernel recreates each time it boots to store information that it needs to run the OS.

However you may be able to help out on the open bug report I have on suspend/resume problems with the 1201N.  Please visit [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921590](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/921590) and add a comment to the bug report describing what you did to make it work.  If you could do it asap that would help because the report will expire in just a couple of days.

You'll need to open a Launchpad account if you do not have one already.

---

### Post by Spamicles on 2012-09-16
You're right. Since I shut down last it doesn't appear to suspend anymore. I marked this as unsolved again and I'll go do the launchpad to post as well.

---

### Post by Toz on 2012-09-16
Have you tried the workaround noted here: [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug")?

According to this arch thread: [https://bbs.archlinux.org/viewtopic.php?id=135543]("https://bbs.archlinux.org/viewtopic.php?id=135543"), tlamer had to make one change to the script to get it to work the his/her 1201n (but that would probably depend on the currently loaded modules).

---

### Post by Spamicles on 2012-09-18
This worked [http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug) but changed but changed DRIVERS="ehci xhci" to DRIVERS="ehci ohci" as mentioned by a comment from someone with a 1201N.

Edit: Screen seems to be flickering a bit now. Had this issue in the past and thought I fixed it with BIOS update and NVIDIA drivers. Could this be a related power or driver issue, or a separate issue from the suspend-fix script?

---

### Post by Toz on 2012-09-19
When exactly is the screen flickering? Is it after the suspend or all the time?

---

### Post by Spamicles on 2012-09-19
I can't seem to replicate it at the moment so maybe it was unrelated. I had this same issue in Windows that a BIOS update and updating Asus power management software seemed to fix.

---

### Post by twipley on 2012-09-19
I remember having had such problems under my own laptop, although I can say that such problems have gone away since quantal beta-1.

I am not 100 % sure that I had the problem under 12.04 and not only in 12.10 alphas, though, but that could well be the case.

/ just an idea.

---

