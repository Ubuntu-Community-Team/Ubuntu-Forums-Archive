---
title: "Problems installing Vista with VirtualBox"
date: 2010-06-10
forum: General Help
---

### Post by blondewarning on 2010-06-10
Now I know the first thing you're going to ask is, "Why on earth are you trying to install Vista?!"  I know, I know, I'd install XP if I had a disc.  My computer came with Vista and I accidentally deleted it when I installed Ubuntu.  Now I'm trying to run Vista as a virtual machine with VirtualBox, but I'm having a bit of a problem.

I'm running Lucid, everything should be up-to-date.  I set up everything in VirtualBox, hit start, and booted up with the CD.  That's where the problems begin.  First screen reads:

> "Windows is loading files..."  
And a little bar at the bottom fills up to completion.  Then I get this:

> "Windows failed to start.  A recent hardware or software change might be the cause.  To fix the problem:

1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance. 

    File: \windows\system32\boot\winload.exe

    Status:  0xc000035a
 
    Info: Attempting to load a 64-bit application, however this CPU is not compatible with 64-bit mode.

I tried copying the disc into an image and booting from that, with the same result.  This is the disc that came with my computer.  I also tried in Virtual Machine Manager, with still the same result.    

I don't know what the 64-bit thing is about.  I'm not sure if I'm running the i386 or AMD version and I don't know which is 64-bit and I don't know how to find out, so that could very well be the problem.  I admit that I'm still a novice at anything linux-related and I apologize for not being more knowledgeable.  Please advise if you have the time.  Thanks!  :)

---

### Post by dcstar on 2010-06-10
VM questions belong in the Virtualization forum.

---

### Post by QIII on 2010-06-10
> **dcstar said:**
> VM questions belong in the Virtualization forum.

That is certainly the case, of course.  But judging from the OPs number of beans, I suspect his familiarity with the forums is limited.  I'll let the moderators move it if they see fit.

As to the problem at hand.

My first question would be whether you are using an actual install disk,  or the "recovery disk" that came with your machine.

Unfortunately, the recovery disks often have something like "...  portions © 20xx Microsoft Corporation..." printed on them.

What that means is that you don't have a retail disk, but an OEM disk.   That means, in turn, that the OEM may have added any number of things  such as drivers, applications and (here's the problem) checks to see if  the OS is being loaded on one of their products.  If you call Microsoft for support when you have a BrandX computer with an OEM disk, Microsoft will tell you to call BrandX and have a nice day.

The long and the short of it is this:  The disk you got with your  machine will often not work with VBox.

That may be one issue.

The second question is the more important.  That is whether you downloaded and installed the VirtualBox version that matches your machine architecture.  Virtualbox comes in 32 and 64 bit flavors.  If your machine architecture is 64 bit but you downloaded and installed the 32 bit version of VirtualBox and are trying to install a 64 bit version of Windows -- you will probably be out of luck.  Your virtual machine will usually behave as if it were a 32 bit physical machine.  It'll puke if you try to install a 64 bit OS.

Can you tell us a little bit about your machine and which version of VBox you have installed?  How about some information on what resources you committed to the virtual machine you are trying to install Windows in?

---

### Post by Mark Phelps on 2010-06-10
If my experience is typical (and I believe it is), I can confirm that you can NOT use an OEM-provided restore disk to install Vista in a virtual disk.  It wants to start be reformatting the whole drive -- which it obviously can NOT do because you're attempting to run it in a virtual disk.

OF course, your disk might be different -- but this situation is the more general case.

However, since Vista came with your machine, the OEM (vendor) might be willing to provide you a full install DVD for a nominal sum.  It wouldn't be free, but it's likely to be a lot less than buying a retail copy.  Worth your checking out.

---

### Post by QIII on 2010-06-10
Personally, the only time I have tried this is with the disk from machine I bought where the OEM actually included an install disk with the Microsoft seal.   I believe that Microsoft's OEM license agreement forbids the installation of the OS via an OEM disk in a virtual environment anyway.  The agreement on my retail disk showed no such proscription.

I'm a "spirit of the law" type of guy, so I wouldn't recommend violating the terms of the EULA on an OEM disk.  You are, after all, agreeing to something even if you think the deal is crap.

I installed Ubuntu over the Windows installation and installed Vista in VirtualBox.  (That way, I only had one Windows installation per that disk, as well.)

---

