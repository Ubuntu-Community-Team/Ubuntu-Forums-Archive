---
title: "Disk troubles in dual boot"
date: 2011-10-23
forum: General Help
---

### Post by Neraste on 2011-10-23
Hello everyone

I have an EeePC 1215B which works fine on my two OS: Ubuntu Studio 11.04 and Windows 7. Each OS has a disk partition and an extra one is designed for data sharing for both system. This data partition has a NTFS file format.

My problem is the following: sometimes, data disappear from this partition, become strangely corrupted or have missing parts. That is really annoying! I have lost important data, such as source codes, reports and lessons because of that...

Two things I have to say:

[LIST]
[*]In Linux, I automount the extra drive with */etc/fstab* configuration file.
[*]For both OS, I enjoy the hibernate function. I often turn a system on, put it in hibernation, open the second one, put it in hibernation, then wake the first one up and so on. Because each OS is better for a specific task ; thought I know this behave is not really good °~° ...
[/LIST]

I suppose the over-use of the hibernate feature is the cause of my troubles. I have some potential explanations and one solution might be to force execution of remaining instructions in disk cache before hibernating. A radical way could be to auto unmount this partition before hibernation and then to auto mount at wake up. How can I do this on Ubuntu?

Moreover, what is your opinion on my problem? Do you have any idea to share data between two OS without troubles?

Thank you for your answers and for your help.

---

### Post by Mark Phelps on 2011-10-24
Hibernation is the core of your problem.  If you're going to SHARE a windows-format data partition between Windows and Ubuntu, then you can not reliably do hibernation, especially of the Windows side.

Why?

Because Windows saves filesystem info when it hibernates. That includes the data partition.  So, any changes made to that partition when Windows is hibernated are going to be UNDONE when it awakens.

In general, dual-booting, shared data partition, and hibernation do not work well together.

---

### Post by Neraste on 2011-10-24
Thank you for your answer, **Mark Phelps**. I agree: my current situation **doesn't work at all** >_< .

I did not know Windows saves filesystem info before hibernating. I understand now... And I guess there is nothing to do against that... But, you said:
> If you're going to SHARE a windows-format data partition between  Windows and Ubuntu, then you can not reliably do hibernation, especially  of the Windows side.Maybe, if I use another filesystem, such as an old one like FAT32 or a non-Windows one like Ext with a kind of driver, can I avoid this behave of Windows?

Of course, the best to do is to avoid hibernating systems. But if there is any trick...

---

### Post by Neraste on 2011-12-23
I have made some tests on Windows to *unmount* a partition before hibernating (thanks to *diskpart* feature) and to prevent filesystem info saving. But unfortunately, it doesn't work and Windows doesn't stop saving filesystem infos.

Well, the true answer to my problem is... To not use hibernating at all between the two OS, as you said, **Mark Phelps**.

---

