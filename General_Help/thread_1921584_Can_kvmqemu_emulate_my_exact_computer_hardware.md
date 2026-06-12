---
title: "Can kvm/qemu emulate my exact computer hardware?"
date: 2012-02-07
forum: General Help
---

### Post by pawanh on 2012-02-07
I want to try to run an OS in qemu and see if it works for the specific hardware I have. My ultimate intention is to install this OS on my Thinkpad; but I don't want to risk my data or waste time in installing only to find out that it doesn't work. I've used Virtualbox in the past, but my knowledge of virtualisation is pretty basic.
So basically, is it possible for kvm to emulate my hardware? What will I need?

---

### Post by dcstar on 2012-02-07
> **pawanh said:**
> I want to try to run an OS in qemu and see if it works for the specific hardware I have. My ultimate intention is to install this OS on my Thinkpad; but I don't want to risk my data or waste time in installing only to find out that it doesn't work. I've used Virtualbox in the past, but my knowledge of virtualisation is pretty basic.
So basically, is it possible for kvm to emulate my hardware? What will I need?

Ask in the Virtualization forum.

---

### Post by 3rdalbum on 2012-02-07
> **pawanh said:**
> I want to try to run an OS in qemu and see if it works for the specific hardware I have. My ultimate intention is to install this OS on my Thinkpad; but I don't want to risk my data or waste time in installing only to find out that it doesn't work. I've used Virtualbox in the past, but my knowledge of virtualisation is pretty basic.
So basically, is it possible for kvm to emulate my hardware? What will I need?

No, it's not possible. Most computer hardware is almost entirely undocumented and the exact workings are unknown to anyone except the manufacturer. It's also not possible to have two operating systems directly accessing the same hardware at the same time - you WOULD lose data.

You've got two options though. Ubuntu comes as a Live CD (or Live USB). When you boot up the Ubuntu CD it actually runs the operating system from the CD. You can test it and see if it runs, if it detects wireless and audio, etc, without touching your hard disk. When you're satisfied, you can double-click the Install icon on the desktop and install it. You can install it side-by-side with Windows; follow the prompts in the installer to make it happen. This is pretty safe and shouldn't result in any data loss.

Warning: Back up all data before installing any operating system, just in case.

Your other option is to do a "Wubi" install. Insert the CD while Windows is running, and a program called Wubi will offer to start. This program can install Ubuntu into a file on your Windows partition. There's no risk of losing data, and in most respects it's a real installation of Ubuntu - it runs directly on the hardware and you'll be able to see if your hardware is compatible.

When you are satisfied, you can remove Wubi using the Add/Remove Programs on Windows and then do a real dual-boot installation like I described, from the Ubuntu live session.

---

### Post by pawanh on 2012-02-07
Thanks a lot for the information. However, I didn't mean Ubuntu. I want to install another OS inside Ubuntu and check. I thought it'd be possible for kvm to directly use my hardware devices (but not the the filesystem) while still running as just a privileged process inside Ubuntu. Is it really impossible? I don't think there is any theoretical constraint against this.

---

