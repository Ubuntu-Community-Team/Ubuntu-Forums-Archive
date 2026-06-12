---
title: "Is VirtualBox best solution for limited Windows needs?"
date: 2012-10-04
forum: General Help
---

### Post by rkashby on 2012-10-04
Hello,

I have had an Ubuntu-only laptop for the last four years and I am now at the point of needing to replace it. I have found that, as much as I would prefer to have nothing to do with Windows, I still need MS Office. (LibreOffice is fine but not truly compatible with Office, which the rest of the world uses. I have learned this the hard way over and over.)

Therefore I have decided I need some access to Windows on the new laptop. Here is my question:

For my limited need for Windows, is the best, safest, and most problem-free solution to install Ubuntu as a replacement for the pre-installed Windows (NOT alongside it as a dual-bootable partition)--and then to download VirtualBox and install Windows within VirtualBox and run it there virtually? 

Or...is the best, safest, and most problem-free solution to set up an Ubuntu partition alongside the pre-installed Windows, and then dual-boot between Windows and Ubuntu?

I would appreciate any advice on which approach would be best. And also suggestion for where I can find clear and current installation instructions for either approach.

(Searching the forums suggests there are problems in either approach, but doesn't tell me whether these problems are rare or frequent, so I am unclear which approach is more likely to be trouble-free for me.)

Thanks very much.

---

### Post by PaulInBHC on 2012-10-04
Depends on what you want to do. I have a mid range box, dual core, 4g ram. I found VB 4.2 easy to install and set up. I have tried XP SP1 (the disc that I have), 8 preview, android-x86. It seems to work well except for 3D apps like games.

I am impatient when it comes to booting and VB seems a quicker way to get to Windows for a once in a while thing. You can do something else while waiting for windows to get started.

---

### Post by kevin2849 on 2012-10-04
The only need I have for a Windows system is to upgrade my GPS software.

I set up the computer with the Windows system, updated everything, then removed that hard drive and set it aside.

I bought another hard drive for installing and using Ubuntu/linux. If I have a need to use Windows (very seldom) I will install the original hard drive, update (takes hours), complete my tasks then reinstall the Linux drive.

For someone needing more frequent access to Windows this is probably not the best solution, but it has worked well for me.

---

### Post by jerrrys on 2012-10-04
I multi-boot and have vBox installed.  They are both good.  Don't think you can go wrong with either way.

About VM's; they will help make testing out things; packages; systems easier.  You have snapshots to work with and its like having a reset button that lets you step back in time quite easily (a few clicks) if things get screwed up.  But there is a learning curve.  And your machine should be atleast dual core with a couple of gig of ram, minimum.  More depending on what your doing.

[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

---

### Post by spaceshipguy on 2012-10-05
I've only tried virtual box, but it works very well and I can swap files with Ubuntu in real time with a shared folder! joy!

---

### Post by 1clue on 2012-10-05
A few years back I needed Microsoft Word and Microsoft Excel on my work system.  I got Crossover Office which is the commercial version of Wine.  It worked perfectly, and I wound up getting Internet Explorer too because of the updates.  That turned out to be handy for testing.

---

### Post by MoebusNet on 2012-10-05
I've been using VirtualBox for a while now, and have never had it screw up my Ubuntu installation. I don't think that the same can be said for setting up a dual-boot system of Windows/Ubuntu. For one thing if I remember correctly, Windows needs to be installed *before* Ubuntu, or Windows won't boot.

I would try the VirtualBox method first; if you can't get it to work you can always uninstall it.

---

### Post by Cheesemill on 2012-10-05
I would go for VirtualBox.

However, one thing to think about is if you have a legal way to install Windows as a guest OS or not.
The recovery disks that you receive with a new laptop (or the recovery disks that you create from your first Windows boot) will almost definitely not work for installing Windows as a VM as they are linked to the physical hardware of your laptop, a VM presents different virtual hardware to the OS so the installation will usually not work.

Even if you do download a Windows install CD that works, the serial number that is printed on your Laptop usually isn't legally usable for a VM, you will probably have to purchase a new copy of Windows to get a legal VM installation.

---

### Post by CrusaderAD on 2012-10-05
Running Windows in a VM works great if you have just a few windows related things you want to do.

---

### Post by fyfe54 on 2012-10-05
> **Cheesemill said:**
> I would go for VirtualBox..

+1

Works very well.  Fast to start, both Win and Ubuntu are running simultaneously and you can share folders between them.

---

### Post by 1clue on 2012-10-05
> **Cheesemill said:**
> I would go for VirtualBox.

However, one thing to think about is if you have a legal way to install Windows as a guest OS or not.
The recovery disks that you receive with a new laptop (or the recovery disks that you create from your first Windows boot) will almost definitely not work for installing Windows as a VM as they are linked to the physical hardware of your laptop, a VM presents different virtual hardware to the OS so the installation will usually not work.

Even if you do download a Windows install CD that works, the serial number that is printed on your Laptop usually isn't legally usable for a VM, you will probably have to purchase a new copy of Windows to get a legal VM installation.

You can remove all occurrences of "usually" from this post and it will be more accurate.

---

### Post by Cheesemill on 2012-10-05
I only put the 'usually' in there because some laptops I work with are supplied by schools or businesses and are covered by the Microsoft Software Assurance program and therefore the OS  ***is*** legally allowed to be run as a VM.

I do agree with you that any PC bought from a normal retailer has a version of Windows that isn't legally allowed to be transfered to a VM (I believe the license conditions have been changed for Windows 8 though).

---

### Post by twipley on 2012-10-05
> Hello,

Hi.

> I have found that, as much as I would prefer to have nothing to do with Windows, I still need MS Office. (LibreOffice is fine but not truly compatible with Office, which the rest of the world uses. I have learned this the hard way over and over.)

Same over here. Office is a must. LibreOffice is fine in and of itself, but it is in most cases not worth the trouble to troubleshoot and solve compatibility issues -- the best method being installing Office.

> For my limited need for Windows, is the best, safest, and most problem-free solution to install Ubuntu as a replacement for the pre-installed Windows (NOT alongside it as a dual-bootable partition)--and then to download VirtualBox and install Windows within VirtualBox and run it there virtually?

Absolutely. Including "safest." I would recommend downloading from their website (latest version; upgradable at wish), then installing Windows, and installing the guest additions (host-key + d).

After that, shut the VM off, set up a permanent shared folder, and perhaps untick "show toolbar in fullscreen" from the advanced settings, and consider entering the full-screen mode for more comfort.

From there, you would be a winner. ;)

---

### Post by MoebusNet on 2012-10-05
> **Cheesemill said:**
> I would go for VirtualBox.

However, one thing to think about is if you have a legal way to install Windows as a guest OS or not.
The recovery disks that you receive with a new laptop (or the recovery disks that you create from your first Windows boot) will almost definitely not work for installing Windows as a VM as they are linked to the physical hardware of your laptop, a VM presents different virtual hardware to the OS so the installation will usually not work.

Even if you do download a Windows install CD that works, the serial number that is printed on your Laptop usually isn't legally usable for a VM, you will probably have to purchase a new copy of Windows to get a legal VM installation.

Hmmm, haven't read the MS license lately (Microsoft free since 2006!) , but it is quite ironic if it is illegal to install Windows in a VM in the same physical machine it was originally bought in. Just sayin'....

---

### Post by Cheesemill on 2012-10-05
It's not really the VM part that is a problem, an OEM copy of Windows is only licensed to the first set of hardware it's installed on.

Because the OEM version that comes with your machine has already been installed on your physical hardware, you can't then install it on a VM because this presents a different set of hardware to the OS.

It is perfectly legal to purchase an OEM copy of Windows and install it only on a VM though.

Also since when when have software licenses been common sense :)

---

### Post by sammiev on 2012-10-05
I per-fer dual boot with Windows as stuff just works and if ubuntu goes down from an update you still have Windows. I use Windows about twice a year.

---

### Post by twipley on 2012-10-05
> **sammiev said:**
> I prefer dual boot with Windows as stuff just works
Stuff "just works" too using VirtualBox -- plus there is an immense breach in terms of security that way. Suppose malware gets inside the Ubuntu system! Sandboxing, without shared clipboard, etc., is really the way to go if one should be using Windows.

> **sammiev said:**
> and if ubuntu goes down from an update you still have Windows.
Getting an extra USB flash drive and leaving the LiveCD on is a better alternative.

Not to sound like "mister who knows all," although I perceive your preference as quite an uninformed one.

---

### Post by 1clue on 2012-10-06
I personally can't stand having to reboot in order to use an app in another OS.  First thing, the frequency with which I need some app in Windows is next to nothing.

Frankly the Crossover Office license is cheaper than any full-blown Windows I know of, and you don't even have to start a VM.

VirtualBox is great if you actually need a VM, but if you just need Office then there's not really any need for that.

---

