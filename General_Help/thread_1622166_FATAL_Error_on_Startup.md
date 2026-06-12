---
title: "FATAL Error on Startup"
date: 2010-11-15
forum: General Help
---

### Post by SteveQuinn on 2010-11-15
When 10.10 starts I get the following error at the top of the screen:

> 
modprobe: FATAL :Could not load /lib/modules/2.6.35-23-generic/modules.dep No such file or dierctory

modprobe: FATAL :Could not load /lib/modules/2.6.35-23-generic/modules.dep No such file or dierctory

It is shown twice on the same screen.

How can I fix this?

I assume it is something to be concerned about especially with the FATAL part being there. After about 10 seconds (not counted) the desktop of 10.10 is shown - no splashscreen or anything there first.

---

### Post by TeoBigusGeekus on 2010-11-15
It's a [documented bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668045").

---

### Post by SteveQuinn on 2010-11-15
**Thanks** I did try and search before making the post but it didn't show anything :confused:

So there is no fix then?

---

### Post by TeoBigusGeekus on 2010-11-15
I'm afraid not (as far as i know). Subscribe to the bug report and update ubuntu daily.

---

### Post by Qrajber on 2010-11-19
Hello guys,

I have to say this is a very strange behavior.
I have got 2 CDs with Ubuntu 10.10, if I install system using the last one downloaded 3 days ago, I have this error at OS start-up. But if I use the other CD, downloaded 3 weeks ago, than I do not see this problem. Both CD are with the same kernel version (2.6.35-22-generic-pae).
I have no idea what is going on...

At the end.. installation were done on the same HW (Lenovo T500).

---

### Post by graffiX on 2010-12-09
Hi there,

Thanks for pointing this out.  I still have this issue with 2.5.35-23-generic.  I have updated to a mainline kernel 2.6.27 rc2 for maverick and the issue seemed to go away.  I don't get the error on boot.

I have a new issue that my acpi temperature sensors don't appear to be working, but I assume that's a separate issue.

Thanks,

Dave

---

### Post by sk4tec on 2010-12-16
Hi,

I'm a totally new Ubuntu user, only been using it 1 hour!! I installed it first on a removable hard drive and it all went ok, so I decided to install on my main disk (win 7 64).

But the install on the Windows 7 disk went fine until the bit where it asks you to remove the Live CD and click ok, I did so it went to the cli screen did some stuff and came up with some errors... I didn't take a photo and i hoped rebooting would fix it. 

Anyhow, I now get the errors on this thread. I understand that its a known issue, but like the previous poster - the first install was fine - but the second wasn't ???

What's the consequence of this problem? Is it a cosmetic issue or a functional issue? Was tempted to re-install, glad I didn't.

---

