---
title: "VirtualBox, Vista, Thinkpad x301 (help?)"
date: 2010-04-23
forum: General Help
---

### Post by amanda on 2010-04-23
Okay, here's the deal.

I got my new Thinkpad and promptly installed Ubuntu over the original OS (Windows Vista). I did keep my rescue partition, but I never made disks.

I'm now discovering that I do need a Windows environment for a few uses (one, actually, but it is unavoidable). I installed VirtualBox, but I don't have any Windows disks. I could buy Windows 7, but just on principle I'm wondering if there's a way to ...? Install from the rescue partion? Install from the rescue disks? 

I know I could just install Windows, full stop, from the rescue partition. But can I use that to create just a .vdi?

It doesn't help that there are a lot of gaps in my picture of what is going on here. The rescue and recovery partition is more than *just* a Windows installer. Or is it?

---

### Post by iponeverything on 2010-04-23
I am not positive on this this, but I think the recovery partition software is set to look for specific hardware before it will install - so if installer finds itself in a vm, it will fail. 

Also, I don't think that you can create an install disk from it.

I could be wrong though:

[http://www.google.com/search?hl=en&source=hp&q=recovery+partition+virtualbox](http://www.google.com/search?hl=en&source=hp&q=recovery+partition+virtualbox)

---

### Post by Mark Phelps on 2010-04-23
> **amanda said:**
> ... I'm wondering if there's a way to ...? Install from the rescue partion? Install from the rescue disks? 

Without examining it it detail, there's no way to know for sure .. but generally, the "rescue partition" installed by PC vendors has the sole purpose of restoring the machine to its original state.  There are generally no options provided for doing anything else.  And in doing that, it very often wipes the hard drive, reformats it, and reinstalls the OS from a custom image.

So, even if you did create a VM, if the rescue operation worked, it would simply wipe and reformat your drive -- not the result you are trying to achieve.
> I know I could just install Windows, full stop, from the rescue partition. 
You're not really "installing" Windows, you're "restoring" it.  Installing provides you a bunch of options; restoration generally does not.

> But can I use that to create just a .vdi?
Probably not .. but don't know for certain.

>  The rescue and recovery partition is more than *just* a Windows installer. Or is it?
See my "installing" remark above ... and yes, it's more than just an installer ...

---

### Post by amanda on 2010-04-26
Well shoot. This sounds like an answer, and not the answer I was looking for.

---

### Post by Jive Turkey on 2010-04-26
Quote:
> The rescue and recovery partition is more than *just* a Windows installer. Or is it?
As a matter of fact its less than that.

You should check the forums at lenovo.  The rescue partition does not work how you might expect.  Having overwritten your windows partition, you have already broken that functionality I'm sorry to say.  As I understand it, you have two options 

1) You'll need to get your hands on a windows install disk (and license) if you want windows back.
2) You might be able to send your HDD to lenovo/IBM to get the default contents re imaged to the disk.

with option 1 you (which actually might be cheaper) you can delete the restore partition, or make your own.

---

