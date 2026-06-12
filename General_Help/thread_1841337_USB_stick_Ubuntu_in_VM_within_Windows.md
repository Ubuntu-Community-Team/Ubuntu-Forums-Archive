---
title: "USB stick: Ubuntu in VM within Windows"
date: 2011-09-09
forum: General Help
---

### Post by Advait on 2011-09-09
Hi All,

I'm pondering the problem of how to browse securely on a probably infected Windows PC (like at an internet cafe or a friend's house, for example). I want to see if there's some way to load a portable Virtual Machine (VM) onto a USB stick that has a write protect switch. The USB stick would have a portable VM (like portable Virtual Box, for example) and then have Ubuntu running within the VM. Then I 1. take this USB stick to a probably infected Windows PC, 2. turn on the write protect switch, 3. insert the USB, 4. fire up the VM and then 5. Fire up Ubuntu and (hopefully) browse securely.

I'm guessing this problem has already been solved, but I haven't seen the solution. Anyone aware of something like this? The key constraint is I want to browse securely on a Windows machine where I'm not able to change the BIOS boot order (it boots straight from the hard drive ignoring the USB and optical drives).

I have an IronKey that does this, but I want to see if it can be done with free software. I'm guessing there's a number of ways to do this. I want to see what's the easiest way for a relative newbie like me.

Thanks!

Tom

---

### Post by haqking on 2011-09-09
> **Advait said:**
> Hi All,

I'm pondering the problem of how to browse securely on a probably infected Windows PC (like at an internet cafe or a friend's house, for example). I want to see if there's some way to load a portable Virtual Machine (VM) onto a USB stick that has a write protect switch. The USB stick would have a portable VM (like portable Virtual Box, for example) and then have Ubuntu running within the VM. Then I 1. take this USB stick to a probably infected Windows PC, 2. turn on the write protect switch, 3. insert the USB, 4. fire up the VM and then 5. Fire up Ubuntu and (hopefully) browse securely.

I'm guessing this problem has already been solved, but I haven't seen the solution. Anyone aware of something like this? The key constraint is I want to browse securely on a Windows machine where I'm not able to change the BIOS boot order (it boots straight from the hard drive ignoring the USB and optical drives).

I have an IronKey that does this, but I want to see if it can be done with free software. I'm guessing there's a number of ways to do this. I want to see what's the easiest way for a relative newbie like me.

Thanks!

Tom

[Damn Small Linux]("http://www.damnsmalllinux.org/") does just that i have it on a USB drive or you can look at a bootable one such as [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

with DSL you just click it and it opens in a window. But it is out of date and not exaclty easy to configure if you are a newbie

or take a look here  [http://www.pendrivelinux.com/using-a-portable-virtualbox-to-run-linux-from-usb/#more-3421](http://www.pendrivelinux.com/using-a-portable-virtualbox-to-run-linux-from-usb/#more-3421) and    [http://www.vbox.me/](http://www.vbox.me/)

---

