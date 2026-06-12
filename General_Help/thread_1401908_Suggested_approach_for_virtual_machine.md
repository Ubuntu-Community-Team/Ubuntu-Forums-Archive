---
title: "Suggested approach for virtual machine"
date: 2010-02-08
forum: General Help
---

### Post by bdemers on 2010-02-08
Not done this before, so looking for possible approaches.

I have need to run XP for some of the specialty apps that I have.  To my chagrin, these are not available, or do not have a reasonable alternative in Linux.  So, having established that, and having tried Wine and failed on some, not all, of the apps, I'd like to move onto using XP in a virtual box.  Not sure, is Ubuntu desktop going to be detrimental in any way or do I use server?  Is there a better virtual machine for Ubuntu desktop running Xp?  Is it possible to control what resources XP uses with the virtual machines backend? I,m assuming that I can install or uninstall drivers inside of XP in a normal fashion, but would like the extra layer.  I want XP as far away from the network as I can get, but Ubuntu will be attached.  I am willing to do file transfers in a round-about fashion in order to keep XP away from the NIC.  Likewise, neither sound nor high intensity video is essential for me, so any compatibility issues regarding audio or video and the virtual software may not be too important to me.  Printing, however, will be essential, this being done via a usb port.

Thanks for suggestions, pointers, etc

---

### Post by rcayea on 2010-02-08
I have always had great success with VMware player for XP. I use it these days to play Football Manager. 

I believe you can control whether or not the network is accessed by your VM in the settings tab of vmware player.

---

### Post by switch10 on 2010-02-08
OK, first of all install VirtualBox from their website.  The OSE version found in synaptic does not have USB support.  

If you want to share directories with ubuntu, you have to set that up under "shared folders" in Settings in virtualbox.

you can disable a network completely if you so desire.  Found in Settings as well.

You are correct about the installing of the windows drivers.  It works the same way.

Yes you control what hardware the virtual machine is alloted.

Do a google search for "vitualbox ubuntu host" and im sure you will find some very good tutorials.

I hope that helps

Dave

---

### Post by rcayea on 2010-02-08
I would politely disagree that you should use VirtualBox. 
Here is why:
VMWARE allows for or has embedded video creation, debugging modes for kernel developers, high speed inter-VM communication via VMCI, solid sound and video support, VM teaming, etc.

This may not have much to do with what you call for, but if VMware is that much better based on the above features, it surely must be better for what you are looking to do. 

In the end, try both, you will find one works best for you. Good Luck!

---

### Post by coldraven on 2010-02-08
I run XP in VirtualBox and it seems to be very good.
If you want USB and fullscreen support you have to install the Guest additions.
I can stretch the window to any size and XP will automatically resize.
I have not tried VMware, I'm not a "power user" but as the man says, try both.
It's really quite simple, even I could do it! ;)

---

### Post by dcstar on 2010-02-09
> **bdemers said:**
> Not done this before, so looking for possible approaches.

I have need to run XP for some of the specialty apps that I have.  To my chagrin, these are not available, or do not have a reasonable alternative in Linux.  So, having established that, and having tried Wine and failed on some, not all, of the apps, I'd like to move onto using XP in a virtual box.
.......

Thanks for suggestions, pointers, etc

Masses of information in the Virualization forum, where all VM issues should be posted.

---

### Post by bdemers on 2010-02-09
Thank you David for the heads up.  In the future, that is where I shall ask this sort of question.  I noticed you have the better part of 8000 posts, whereas I have around 80.  I'm not quite as familiar, sorry.  In the meantime I do Have some response, enough to get started I guess. I'll mark the post solved

---

### Post by anubis2497 on 2010-02-09
they have vm ware for linux
or install virtualbox install xp to it install guest aditions then run in seamless mode or not its optional and go make a network shared folder through virtual box while xp is loaded and share files to and frome ubuntu to xp in virtual just boot xp and go to run and type in explorer and go to network places and bring down the tabs and your sharing and u can run your xp programs.

---

