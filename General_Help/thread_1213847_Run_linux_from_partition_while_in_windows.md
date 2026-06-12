---
title: "Run linux from partition while in windows?"
date: 2009-07-15
forum: General Help
---

### Post by thunderbirdje on 2009-07-15
Hi!

I've installed Ubuntu on a separate partition.

I was wondering if it's possible from within windows (my other partition) to run 'virtual' linux in a windows using that existing linux partition? I mean without rebooting (select Linux in GRUB menu, going throug disc checks...). I have to switch often between both operating systems and It would be great if I could virtually access my linux partition without rebooting.

I know they are some linux boxes available for Windows, but I would like to keep my real Ubuntu partition (emulation doesn't come out always perfect when it comes to networking, etc...)

Thanks!

---

### Post by nikhilk on 2009-07-15
Running two REAL operating systems simultaneously is not possible. Using a virtual machine seems to be your best bet.

---

### Post by thunderbirdje on 2009-07-15
Is it possible to "connect" a virtual machine with an existing ubuntu partition? 

Or do I better say: to run a partition with ubuntu in a virtual machine?

---

### Post by nikhilk on 2009-07-16
> **thunderbirdje said:**
> Or do I better say: to run a partition with ubuntu in a virtual machine?

Sorry, I have very little experience with virtualization, so I do not have much idea. But I think you need an image/virtual appliance of some sort to run in a virtual machine. e.g. VMware products (VMware Player, VMware Workstation) require a ".vmx" file along with several others.
I do not know about other virtualization solutions, so if someone can elaborate that will be great.

---

### Post by mcduck on 2009-07-16
> **thunderbirdje said:**
> Is it possible to "connect" a virtual machine with an existing ubuntu partition? 

Or do I better say: to run a partition with ubuntu in a virtual machine?

It is possible, although needs some of hacking to get it working. But the big issue here is that the virtual machine hardware is different from your real hardware which causes a load of problems (graphics card drivers for real graphics card versus the virtual one, drive mappings in the real setup versus virtual machine, drivers for all your hardware, network interfaces of the real machine versus virtual machine etc).

---

### Post by zwdev on 2009-07-17
thunderbirdje,

I have a similar setup on my machine but the difference is I have linux and w1nd0w$ on a seperate partition that I use as a virtual machine as well as a physical machine. This is fairly easy to achieve. I would advise you to do it this way to realise the full power of UBUNTU. You will not miss the physical windows machine, on her laptop my wife does not.
:-)

---

### Post by thunderbirdje on 2009-07-17
> **nikhilk said:**
> Sorry, I have very little experience with virtualization, so I do not have much idea. But I think you need an image/virtual appliance of some sort to run in a virtual machine. e.g. VMware products (VMware Player, VMware Workstation) require a ".vmx" file along with several others.
I do not know about other virtualization solutions, so if someone can elaborate that will be great.

I also have little experience :-) Thanks for helping!

> [QUOTE]It is possible, although needs some of hacking to get it working

Which software do you use? And what kind of hack?

[QUOTE]I have linux and w1nd0w$ on a seperate partition

Zwdev, so do I :D Nice! Can you tell me which software you use? If I'm understandig correct you have a *Windows partition* and an *Ubuntu partition*? Which kind of software did you install on which partition? And I guess it's possible to run a physically partition virtually? :D This sounds nice and as a solution to my situation :D :D

---

