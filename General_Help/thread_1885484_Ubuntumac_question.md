---
title: "Ubuntu/mac question"
date: 2011-11-23
forum: General Help
---

### Post by jmcgee41 on 2011-11-23
I asked this in the Apple section but no one seems to know, perhaps it will have better luck here.

I download the live cd and ran it first and was quite pleased with what came up. So after playing with it a bit i went ahead and installed it in Parallels. I have a question to start off with:

1. With the live cd all my mac drive partitions were shown and usable, but after the install they do not show any longer. Did i do something wrong in the install ? or is there something i need to do in order to get them back ?

Thanks for any help you can give...

---

### Post by BC59 on 2011-11-23
> **jmcgee41 said:**
> I asked this in the Apple section but no one seems to know, perhaps it will have better luck here.

I download the live cd and ran it first and was quite pleased with what came up. So after playing with it a bit i went ahead and installed it in Parallels. I have a question to start off with:

1. With the live cd all my mac drive partitions were shown and usable, but after the install they do not show any longer. Did i do something wrong in the install ? or is there something i need to do in order to get them back ?

Thanks for any help you can give...

It's not the same.

Live CD is running the computer like a normal OS, but a virtual machine is an OS running inside another OS. We are speaking now for 2 different computers.

So now to communicate with your computer through the virtual machine, you can do it through a Network. It's like connecting 2 different computers.

Just check the guide of Parallel on how to do it.

---

### Post by Frogs Hair on 2011-11-23
Hi jmcgee41

I am not a Mac user , but when you installed Ubuntu did you create a partition or use the entire disk ? If you used the second option then the entire disk was formated . You can check the system monitor under file system or the disk utility to view current status .

---

### Post by 3rdalbum on 2011-11-23
Parallels is a virtual machine; it doesn't allow the guest OS to access the host OS's disk/partitions directly. Basically, it's because of the risk of the host OS (the one running directly on the hardware) and the guest OS to both attempt to write to disk at the same time, destroying your data.

Most virtual machine programs have a "shared folder" function where a folder on the host OS appears to the guest OS as a network share; you could try this.

However, it kinda sounds like you want Ubuntu running directly on the hardware, but thought that Parallels was the only way to have Ubuntu installed. Parallels is useful for running multiple operating systems simultaneously, but I think what you might be after is a "dual boot" where, when you boot up, you get the choice of whether to run Ubuntu or OS X.

I haven't used Ubuntu on an Intel-based Mac so I can't advise you how to arrange a dual-boot scenario. Maybe you could look on Google for "dual-boot ubuntu mac" and follow the directions you find for that version of Ubuntu you want to use. Don't use one from a different version though; things change in Ubuntu very quickly. Alternatively, the people in the Apple section of the forum might be able to point you in the right direction.

---

### Post by jmcgee41 on 2011-11-23
Thanks for the response guys, i kind of thought that was the case, but just wanted to be sure before i go making a lot of changes that could do more damage.

---

