---
title: "i need assistance"
date: 2010-01-03
forum: General Help
---

### Post by 0712456 on 2010-01-03
[SIZE=2]hi ubuntu user I am a new user for ubuntu and i have few questions ineed Answers [/SIZE]

[SIZE=2]1-how can i open device manager ? :confused:[/SIZE]
[SIZE=2][/SIZE] 


[SIZE=2]2-is ther abrograms like win zip on ubuntu?:confused:[/SIZE]
 


[SIZE=2]3- how i now if all the dvice are [SIZE=2]Installed on my computer?:confused:[/SIZE][/SIZE]

---

### Post by MelDJ on 2010-01-03
archive manager can open up zips

---

### Post by warfacegod on 2010-01-03
> 1-how can i open device manager ?



2-is ther abrograms like win zip on ubuntu?



3- how i now if all the dvice are Installed on my computer?



1. Ubuntu doesn't have a device manager installed by default I don't think. Use ubuntu software center and search for device manager.

2. It's called Archive manager.

3. See answer 1 that might be the easiest.

---

### Post by Leppie on 2010-01-03
if not already installed, install gnome-device-manager:
```
$sudo apt-get install gnome-device-manager
```

---

### Post by Bartender on 2010-01-03
Hoo boy -

Hopefully the hardest thing for you will just be general disorientation and confusion, not any real hardware problems.  There are several concepts you'll need to internalize before Linux begins to make sense.  As long as you keep looking for the "Windows button" it'll seem confusing.  

After getting over that initial confusion, I've found that the way things are laid out in Ubuntu makes MORE sense than Windows.  It's just a matter of finding your way and remembering how you got there.

A couple of big changes - unlike Windows, you will not need to muck about in any part of the file system for day-to-day operation.  You have your Home folder, and that's all you need to know unless you need to know more if you know what I mean.

When adding programs, you're not going to be going out on the web and finding .exe's that you can download and double-click on.  For the new user, it's best to just stick to Update Manager, Synaptic, and Add/Remove.  Unless you installed 9.10, which has the new Ubuntu Software Store.  I'm not familiar with the Store, but it's supposed to be easier than what came before it.  When you stick to the Ubuntu repositories you can feel pretty darn sure that anything you download/install will "just work".

As a Windows user, I kind of miss the Windows Device Manager.  There's not really a similar interface in Ubuntu that lets you disable hardware, try to fix it, etc.  gnome-device-manager does function as a list of devices, but it's not for tweaking on those devices.

7-zip is an open-source unzip utility, available via the repositories.

How will you know if all your devices are installed?  Well, did they work??  The driver situation is also a _lot_ different than what you're used to.  In a nutshell, if some device isn't supported natively or via the Hardware Drivers utility in System>Administration, you might find it difficult to get something working.

---

