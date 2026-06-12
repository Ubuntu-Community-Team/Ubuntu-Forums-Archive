---
title: "Empty Grub at Startup"
date: 2012-06-23
forum: General Help
---

### Post by melody10511 on 2012-06-23
Hi there. I have this problem where when I start my laptop, before launching Ubuntu it shows a blank purple screen for about 15 seconds. I know this is where the boot manager is supposed to be since I've used Ubuntu before. But it's just plain empty now: no cursor, no nothing. I've tried pressing shift or any button for that matter and it doesn't show up.

Here's the whole story:

I formatted my Windows 7 and reinstalled Ubuntu 12.04 a while ago. After this, the laptop showed the Windows boot manager on startup. I didn't want this so I just disabled the boot manager on Windows. After that, the boot manager didn't show up but the problem stated above started. So now I can't get to my Windows 7.

I've been searching through the net, and I tried Boot Repair. It doesn't work. I've tried editing etc/default/grub and it seems that I can't change it because of some authentication error. (I don't know how to open it as sudo)

More strangely, my Boot Repair has GRUB location and GRUB options disabled (as in it's empty and it's grey) and has MBR option on. Problem is, I don't know how MBR works either.

Can anyone please help me? Kinda urgent here...

---

### Post by blackflame2996 on 2012-06-23
you can use a super grub2 live disk to access the operating systems.
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by melody10511 on 2012-06-23
I'll try that, but will it be my boot manager on start up? I don't want to open Ubuntu to open Windows again.

---

