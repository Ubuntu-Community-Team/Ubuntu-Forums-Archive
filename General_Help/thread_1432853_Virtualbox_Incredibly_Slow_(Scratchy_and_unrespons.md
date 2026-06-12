---
title: "Virtualbox Incredibly Slow (Scratchy and unresponsive)"
date: 2010-03-18
forum: General Help
---

### Post by DNCashman on 2010-03-18
Has anyone had any issues when they freshly install Windows XP in VirtualBox?

I just created a system in vBox with an AMD x4 925 2.8Ghz Quadcore Processor (with AMD Virtualization on). I gave the system 3 cores, 3GB of RAM, 128mb video memory, turned off all acceleration and gave it a 60GB virtual drive.

Following installation I have noticed the vbox is unusable. I click on the start menu for example and it takes 3-4 seconds to show up. Furthermore, just moving the mouse shows a frame rate at, what I would guess, around 5 frames/sec.

This is strange as I have given this machine very good specs. What would be the case do you think? Any help very appreciated!

---

### Post by Tikkyca on 2010-03-18
Install guest edition.

---

### Post by Warthaug on 2010-03-18
> **DNCashman said:**
> Has anyone had any issues when they freshly install Windows XP in VirtualBox?

I just created a system in vBox with an AMD x4 925 2.8Ghz Quadcore Processor (with AMD Virtualization on). I gave the system 3 cores, 3GB of RAM, 128mb video memory, turned off all acceleration and gave it a 60GB virtual drive.

Following installation I have noticed the vbox is unusable. I click on the start menu for example and it takes 3-4 seconds to show up. Furthermore, just moving the mouse shows a frame rate at, what I would guess, around 5 frames/sec.

This is strange as I have given this machine very good specs. What would be the case do you think? Any help very appreciated!

By "I gave the system 3 cores, 3GB of RAM..." I assume you mean that you gave the guest the 3 cores, etc?  Without knowing all the details of your system it is possible (aside from not having guest addons installed) that you may not have left enough resources for your host.  Check your settings (VBox usually warns you if you're giving too little to host or guest).  You can also try dialing back the number of cores/memory your are running to see if that helps.

But if you've not installed guest addons, do that first.  That fixes most non-user error type issues.

Also, try pausing/stopping any programs your host is running in the background that are not needed for the host itself.  For example, I run [boinc]("http://boinc.berkeley.edu/") on my computer, and I get the same behaviour as you describe if I don't pause it while running XP in vbox.

Bryan

---

### Post by DNCashman on 2010-03-18
> **Warthaug said:**
> By "I gave the system 3 cores, 3GB of RAM..." I assume you mean that you gave the guest the 3 cores, etc?  Without knowing all the details of your system it is possible (aside from not having guest addons installed) that you may not have left enough resources for your host.

VBox did give me a warning but my machine specs are:

AMD PhenomII x4 925 (2.8Ghz Quad Core)
5GB DDR2-800 RAM
512MB nVidia GeForce 9400GT

I have changed my install to Win7 and experienced the same issues. I ran the system monitor and noticed that one of my cores is always at 100% (the core involved fluctuates, sometimes 1st, sometimes 2nd, 3rd etc).

> **Warthaug said:**
> But if you've not installed guest addons, do that first.  That fixes most non-user error type issues.
Hmm what are these guest addons? Anything specific I should be looking atm?

Its always strange that my install discs are always smoooth and fast (ie. the mouse is perfectly smooth), whereas the system is very slow (mouse is like 5 fps).

---

### Post by acroporas on 2010-03-18
Virtual-box was allays unusably slow for me as well.  Then I moved the virtual hard drive to an Intel x25M SSD and it suddenly became nice and snappy....

---

### Post by blur xc on 2010-03-18
> **acroporas said:**
> Virtual-box was allays unusably slow for me as well.  Then I moved the virtual hard drive to an Intel x25M SSD and it suddenly became nice and snappy....

Funny- all of my VM's are smooth and snappy...and I didn't do anything fancy to get them that way...  Both Windows hosts, Linux guests, and vice versa...

BM

---

### Post by bmuluu on 2010-03-18
> **DNCashman said:**
> 
Hmm what are these guest addons? Anything specific I should be looking atm?

Guest additions are packages that prepare a guest OS to fully
utilise the resources handed to it by its host.
When running a virtual machine, hold down the host key 
with D - the Right Control button in my case [Ctrl + D], 
that should mount the
Virtual Box Guest Additions CD in the guest machine.
The additions when installed provide drivers and other software
needed to make the guest OS more usable.

---

### Post by DNCashman on 2010-03-18
> **bmuluu said:**
> Guest additions are packages that prepare a guest OS to fully
utilise the resources handed to it by its host.
When running a virtual machine, hold down the host key 
with D - the Right Control button in my case [Ctrl + D], 
that should mount the
Virtual Box Guest Additions CD in the guest machine.
The additions when installed provide drivers and other software
needed to make the guest OS more usable.

Hey mate, just installed the Guest additions and still its scratchy and unusable :S

Any other things I could consider?

---

### Post by ManyuX95 on 2010-03-18
I think I know the problem! It is called Windows :P jaja well, what you said also kind of happened to me, why dont you use wine?or maybe you can install windows better [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) (hope it helps)

---

### Post by diablo75 on 2010-03-18
How much virtual memory did you tell Virtualbox to give your VM?  If you give the VM more memory than the system can physically provide it, Linux starts using the swap partition LIKE MAD and makes EVERYTHING (the VM and your own Linux system) run very slowly.  If you've got 3 GB of RAM to play with, don't give your VMs any more than... oh... half of that.  1.5 GB MAX.

Edit to add:  Make sure your your guest OS is running as bare-boned as possible.  Get rid of that side-bar crap, shut off the little IM apps, any little utility software you don't use or need, run msconfig and uncheck a bunch of stuff in the Startup tab, things like that.  I've never run Vista in a VM, but XP runs superbly as does Windows 7.

---

### Post by alaricd on 2011-01-02
Has any one had any luck with this?  I have yet to find a usable post to help with this...  The real problem is this.

Same VirtualBox on 2 different OSes, same specs all the way around (dual boot machine)

Disk Throughput on Windows Guest on Ubuntu Host - 13 MB/s
Disk Throughput on Windows Guest on Windows Host - 80MB/s

It looks like this has been going on a while, as of this writing I am using a fully up-to-date Maverick Meerkat installation, and just upgraded my Virtualbox to 4.0.

---

