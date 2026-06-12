---
title: "Dual boot Ubuntu - Virtual machine question"
date: 2011-05-18
forum: General Help
---

### Post by DeadlyBreakdown on 2011-05-18
i have ubuntu 11/ win7 dual boot. Is there anyway to log into my windows 7 partition while on Ubuntu? This would be EXTREMELY helpful. thanks.

---

### Post by dcollier on 2011-05-18
are you trying to access the windows file system?  if so just open your home folder and navigate to the directory.

---

### Post by dcollier on 2011-05-18
I should say click on the image of your hd, you should see your hd listed in the home folder

---

### Post by DeadlyBreakdown on 2011-05-18
I understand i can access the files - but I want to do various tasks that can only be done within applications such as exporting bookmarks from chrome on win 7, and exporting my iTunes library.

---

### Post by Joe of loath on 2011-05-18
No, Windows' activation program detects the change in hardware, and decides you've moved the disk to a different PC, before giving you three days to buy a new license.

---

### Post by dragonfly41 on 2011-05-18
You can "sync" your chrome bookmarks between windows and ubuntu.

---

### Post by CTBuckweed on 2011-05-18
> **Joe of loath said:**
> No, Windows' activation program detects the change in hardware, and decides you've moved the disk to a different PC, before giving you three days to buy a new license.

I have no experience with Windows 7. I still use XP at home for things I that I must do in Windows.

I have successfully done a complete backup of XP and restored it, even to a different drive type (from SCSI to a new SATA). As long as Windows still sees it as the same drive letter (C: D:, etc.) it will still work okay. On Windows 7, I have no idea.

Microsoft is so paranoid about someone making and using a copy Windows. Their draconian efforts to prevent illegal copying of their software has even bitten me just when I switched to a new graphics card. I had to reactivate XP because of the hardware change-out.

I now pretty much run my Windows XPs as a guest OS in VirtualBox. I have an old MSDN universal license that gives me unlimited XPs, dev studios, etc. for development use. To skip entering the license number and the reactivation for each new XP, I have a VM image of an activated XP with nothing else and use it as a base to create my additional VMs. It saves a lot of time and frustration.

I activated my XP so many times, I ran out of activations, even though the MSDN provides for unlimited use - I had to call Microsoft to get a new XP license key for my XPs bundled with MSDN.

---

### Post by CTBuckweed on 2011-05-18
> **dragonfly41 said:**
> You can "sync" your chrome bookmarks between windows and ubuntu.

I regularly sync my Firefox between ubuntu and XP. I run both FFv4.0.1 and v3.6.xx on my XPs and v3.6.17 on unbuntu 64 bit.

I don't know about Chrome...

---

### Post by perspectoff on 2011-05-18
A related question:

If you create a Windows virtual machine and use that virtual machine instance to register a copy of Windows, can you then use that Windows virtual machine image anywhere? Can you then replicate the image?

In other words, does Windows recognize the virtual machine settings as its hardware in determining if the copy of Windows is legitimate?

If so, one could register one copy of Windows from a virtual machine and then replicate it many times. Problem solved. I don't have $200-300 for a new Windows OS to experiment with, but if someone has tried it, it would be useful to know.

My answer to the OP's original question has always been the opposite.

If a user is that dedicated to Windows, they should run (K)Ubuntu from within Windows (not the other way around). In that case, run a Virtualbox/VMWare/QEMU virtual machine from within Windows in which you can install (K)Ubuntu, or use Wubi to install (K)Ubuntu so that it runs as an "application" within Windows.

---

### Post by CTBuckweed on 2011-05-18
> **perspectoff said:**
> A related question:

If you create a Windows virtual machine and use that virtual machine instance to register a copy of Windows, can you then use that Windows virtual machine image anywhere? Can you then replicate the image?

In other words, does Windows recognize the virtual machine settings as its hardware in determining if the copy of Windows is legitimate?

If so, one could register one copy of Windows from a virtual machine and then replicate it many times. Problem solved. I don't have $200-300 for a new Windows OS to experiment with, but if someone has tried it, it would be useful to know.

My answer to the OP's original question has always been the opposite.

If a user is that dedicated to Windows, they should run (K)Ubuntu from within Windows (not the other way around). In that case, run a Virtualbox/VMWare/QEMU virtual machine from within Windows in which you can install (K)Ubuntu, or use Wubi to install (K)Ubuntu so that it runs as an "application" within Windows.

Yes, I do that here (clone XP virtual machines) at home. I have multiple XP guests on my Linux machine that I run for various purposes and for testing.

I have never have tried to actually use a guest VM image of XP on a different machine running 'Virtual Box', but I would venture to guess that it would work. Virtual Box presents an identical guest 'machine' so a cloned XP just 'thinks' it's on the same machine. I am not suggesting that this is a way to duplicate and run multiple XPs with just a single license of Windows XP. Here, I have a **valid** MSDN Universal license that allows me to install an unlimited amount of XPs for personal development use.

I have a disk image of a virgin, but activated XP with SP3 and hot fixes installed. For a new virtual machine, I clone the disk image to to make a new virtual machine. It saves me from having to type in the license key and activate it.

**Once again, _I am not suggesting, nor am I recommending to anyone that this is a way circumvent the Microsoft licensing terms of XP so that multiple instances of XP may be installed and run._ The user is allowed to run only as many XPs as he has licenses. Doing so would violate the terms of the Microsoft licensing agreement for XP. For more details of XP licensing, refer to the Microsoft licensing agreement for XP.**

---

### Post by wildmanne39 on 2011-05-18
> **perspectoff said:**
> A related question:

If you create a Windows virtual machine and use that virtual machine instance to register a copy of Windows, can you then use that Windows virtual machine image anywhere? Can you then replicate the image?

In other words, does Windows recognize the virtual machine settings as its hardware in determining if the copy of Windows is legitimate?

If so, one could register one copy of Windows from a virtual machine and then replicate it many times. Problem solved. I don't have $200-300 for a new Windows OS to experiment with, but if someone has tried it, it would be useful to know.

My answer to the OP's original question has always been the opposite.

If a user is that dedicated to Windows, they should run (K)Ubuntu from within Windows (not the other way around). In that case, run a Virtualbox/VMWare/QEMU virtual machine from within Windows in which you can install (K)Ubuntu, or use Wubi to install (K)Ubuntu so that it runs as an "application" within Windows.
Hi, if I got your question right the answer is no, even in the same virtual envirnoment if you say change most settings after it is set up it will tell you to reactivate.

---

### Post by Chiphead2011 on 2011-07-21
I happend to run across the following article while looking for a solution to a completely different problem.
 
I HAVE NOT TRIED THIS and it applies to XP but maybe it will give you some hints/tips to get you moving.
 
[http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)
 
Regards

---

