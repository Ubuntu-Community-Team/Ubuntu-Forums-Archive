---
title: "How to get USB scanner support with a VirtualBox Windows XP Guest, Lucid Lynx Host"
date: 2010-05-11
forum: General Help
---

### Post by Matt G Dalian on 2010-05-11
This is building off this thread:
[http://ubuntuforums.org/showthread.php?t=1445314&page=2](http://ubuntuforums.org/showthread.php?t=1445314&page=2)

The problem:

Running VirtualBox on Ubuntu Lucid Lynx 10.04, installing a Windows XP guest (or any guest system), the virtual OS was unable to detect my HP scanner (USB).

I fixed it following the instructions in comment #12 on the thread above.

You need VirtualBox 3.1.8 or above. If it's not in the repository you can download it from [www.virtualbox.org]("http://www.virtualbox.org")
This fixes the USB problem in Ubuntu 10.04 (something about Lucid not using HAL, which earlier versions of VirtualBox required for USB support).

1. Run VirtualBox as superuser
$sudo VirtualBox

2. Install any OS
(I installed Lubuntu)

3. Plug in your scanner (or other USB device) and in the lower right hand corner click on the USB icon to activate it.

And you're done.

Now when you run VirtualBox as a normal user (no root privileges) it will detect your USB device.

BUT there's one more catch if you want to use Windows XP (or another older OS):
**Under the virtual OS settings, you can't have USB 2.0 checked off**. Windows XP can't detect USB if it's set to use 2.0.


Finally, I'm not sure if this affected anything, but under Users and Groups I created a new group called "vboxusers" and added myself to it (this is also discussed in the thread above).

Hope that helps.

---

