---
title: "Folder Tasks"
date: 2010-12-15
forum: General Help
---

### Post by cracker89 on 2010-12-15
Is there any way to do the following:

Say there is an external harddisk, the filesystem is of no specifities. Say I want to make a folder on it such that it can only be viewed on Linux systems and not on windows systems.

Its of some usefulness, everyone else at my home uses winders :P

Appreciated.

---

### Post by zeroseven0183 on 2010-12-15
Setting folder permissions or password-protecting it would do.

---

### Post by cracker89 on 2010-12-15
but then thats not reading it. is there a way it can see all folders except a certain set

---

### Post by zeroseven0183 on 2010-12-15
Well, the only thing I can think of is by reformatting the hard drive to a file system not recognized by Windows, that is, ext4 or something other than NTFS and FAT32.

You can also just resize the partition, format it to ext4 and put the files there.

---

### Post by cracker89 on 2010-12-15
That is a very good idea, and will suffice for my purposes. 
Thanks...

However, as a matter of knowledge, is there some way to do it the other way..? 

Ok, for example, if i insert an external disk into a windows machine which is teeming with viruses, I often see various exe's and folders not visible on the windows machine..? Not that I am making viruses here, lol, but as a matter of information and knowledge..

---

### Post by zeroseven0183 on 2010-12-15
> **cracker89 said:**
> That is a very good idea, and will suffice for my purposes. 
Thanks...

However, as a matter of knowledge, is there some way to do it the other way..? 

Ok, for example, if i insert an external disk into a windows machine which is teeming with viruses, I often see various exe's and folders not visible on the windows machine..? Not that I am making viruses here, lol, but as a matter of information and knowledge..

I'm sorry, but I think, I need some clarifications on that. What do you mean?

---

### Post by cracker89 on 2010-12-15
Sorry, wrote that out in a hurry. 

My friend has a machine with windows in it. It is virus infested, intensely so. If I ever take any data from his machine, say on a pendrive, and then when I insert the pendrive in my Ubuntu machine, I often see folders and exe's that weren't originally there before I inserted it in the infected windows machine, nor when the pendrive was connected with the windows machine.

How does that work?  Does this make sense?

Thank you for trying.. :P

---

### Post by QLee on 2010-12-16
[QUOTE=cracker89]Sorry, wrote that out in a hurry.[/QUOTE]

A piece of advice, don't hurry when asking questions on a forum. Lots of people don't have English as a first language (but may have good answers) and need things to be clear in order to be able to help, even though this is an English Language forum. In the long run, the time you use to be clear will be worth it.

[QUOTE=cracker89]My friend has a machine with windows in it. It is virus infested, intensely so. If I ever take any data from his machine, say on a pendrive, and then when I insert the pendrive in my Ubuntu machine, I often see folders and exe's that weren't originally there before I inserted it in the infected windows machine, nor when the pendrive was connected with the windows machine.

How does that work?  Does this make sense?...[/QUOTE]

It is possible to have both hidden files and directories(folders) on Windows and it can be useful for a rootkit and/or other malware to try and hide that way as many Windows users don't know that.

---

### Post by theozzlives on 2010-12-16
I'd say, if your friend refuses to clean his machine, DON'T get any files from such a person!

---

### Post by cracker89 on 2010-12-16
> **QLee said:**
> A piece of advice, don't hurry when asking questions on a forum. Lots of people don't have English as a first language (but may have good answers) and need things to be clear in order to be able to help, even though this is an English Language forum. In the long run, the time you use to be clear will be worth it.



It is possible to have both hidden files and directories(folders) on Windows and it can be useful for a rootkit and/or other malware to try and hide that way as many Windows users don't know that.


Yes sah! Was running late for an exam. 

Right, yes, windows has the option to hide files, but thats not the usual way under folder properties (i think), is it?

How is that done?

And yes, I dont take files from him, will soon boot up ubuntu on his machine too.

---

### Post by veggen on 2010-12-16
Those files/folders are either just common hidden files or were maybe labeled as system files (attrib +s filename), so Windows won't see them by default. Linux doesn't care for those attributes so it will show the files/folders anyway.
In Linux, you hide files by prefixing their name with a dot. But they'll be visible in Windows since it doesn't care for this convention. So, do what was already suggested, make a small partition that is ResierFS (for example) and put stuff there. Windows will have hard time seeing that (but it's still possible).

---

