---
title: "Help Virtual Machine and others"
date: 2009-12-07
forum: General Help
---

### Post by blues_1pt on 2009-12-07
Hello, i used and reused ubuntu in toher machines....but now i wat to install at my computer. I have Asus W5F, Core Duo at 1.83 GHz, 1Gb RAM and 100 Gb disc. I want to install ubuntu but i also want to install a Virtual Machine fo Windows. I want to know if anyone knows a lighter but also good virtual machine. And after I have windows XP working as a virtual machine, does anyone knows how to put internet working inside the virtual machine.
The last question, does anyone knows how to make a shared partitition of the disc at Ubuntu and then i also can use it at Windows (inside the VM)?
Thank you, and sorry for this BIG question.  :)

---

### Post by t0p on 2009-12-07
> **blues_1pt said:**
> I want to install ubuntu but i also want to install a Virtual Machine fo Windows. I want to know if anyone knows a lighter but also good virtual machine.

I like VirtualBox.  When I was reading about it, I was advised to use the closed-source version if I wanted USB support.  So I installed the closed-source version, available from [virtualbox.org]("http://virtualbox.org") - ie *not* the version in the repostories.

> **blues_1pt said:**
> 
 And after I have windows XP working as a virtual machine, does anyone knows how to put internet working inside the virtual machine.


Once you've got your virtual XP installed, it will automatically use your host (Ubuntu) internet connection.  No set up required.

---

### Post by blues_1pt on 2009-12-07
Thanks for your reply. But do you think that my computer will not stay just a little bit slow? I tried once VMWare i my pc staied slow as hell.

---

### Post by t0p on 2009-12-07
When you're running a guest operating system in VMWare or VirtualBox, you are in effect running 2 operating systems on one computer.  And those 2 OSes have to share the resources of that computer.  So when you are running an XP virtual machine, of course your computer will run slower.

When you're setting up the virtual machine, you can set how much of the computer's RAM you want to let virtual XP use.  You need to make sure you leave enough for your host (Ubuntu) to carry on working okay.  For example: let's assume your computer has 2 GB of RAM.  If you let virtual XP have 1 GB, that'll leave 1 GB for Ubuntu.  Should be fine.  But if you gave 1.5 GB to virtual XP, that would leave only 0.5 GB for Ubuntu.  Not so good.

So you need to make sure you leave the host (Ubuntu) with enough resources.

---

### Post by blues_1pt on 2009-12-07
Yeah you're right, but since i have only 1 Gb of ram.........mmmmmmmm.......the most would be 50% for each, but that isn't enough.

---

### Post by stav1953 on 2009-12-07
Hope to be in the right thread, if not admin, please feel free to move.

Here is my problem: trying to install virtualbox on Ubuntu 9.10 in order to run some windows apps. Installation runs OK but during windows updates I get the error message that "The volume Filesystem root is full". My c: drive is NTFS and has 50GB so cannot be full. what's the workaround?
My system has 4GB RAM (1GB allocated to windows) and 640GB HDD (50GB allocated to windows). I had the same problem with VMware Player. Any Linux guru out there willing to help? Thanks.

---

### Post by snowpine on 2009-12-07
> **stav1953 said:**
> Hope to be in the right thread, if not admin, please feel free to move.

Here is my problem: trying to install virtualbox on Ubuntu 9.10 in order to run some windows apps. Installation runs OK but during windows updates I get the error message that "The volume Filesystem root is full". My c: drive is NTFS and has 50GB so cannot be full. what's the workaround?
My system has 4GB RAM (1GB allocated to windows) and 640GB HDD (50GB allocated to windows). I had the same problem with VMware Player. Any Linux guru out there willing to help? Thanks.

Your virtual machine uses a virtual hard drive (not your computer's "real" hard drive).

When you first set up the virtual machine, you were asked how large to make the virtual hard drive. In the main VirtualBox control window, right click on the machine, choose Settings, Storage. You'll see how large the virtual drive is.

---

### Post by stav1953 on 2009-12-07
Thanks for the quick answer,
Please see the png attached. I still have more than 3GB of space, if need more how to change it in Ubuntu?
Thanks again,
Stav

---

### Post by snowpine on 2009-12-07
> **stav1953 said:**
> Thanks for the quick answer,
Please see the png attached. I still have more than 3GB of space, if need more how to change it in Ubuntu?
Thanks again,
Stav

Ah, I misunderstood the question. You have plenty of space in the Windows virtual drive.

I think your physical Ubuntu partition is full though. :)

---

### Post by stav1953 on 2009-12-07
> **snowpine said:**
> Ah, I misunderstood the question. You have plenty of space in the Windows virtual drive.

I think your physical Ubuntu partition is full though. :)

If I understand you correctly, this is the HDD of the host (Ubuntu 9.10). There I have 640GB and 292GB free, so this is not it. Anything else I should be looking at?[IMG]file:///home/stavros/Desktop/HDD.png[/IMG]

---

### Post by snowpine on 2009-12-07
> **stav1953 said:**
> If I understand you correctly, this is the HDD of the host (Ubuntu 9.10). There I have 640GB and 292GB free, so this is not it. Anything else I should be looking at?[IMG]file:///home/stavros/Desktop/HDD.png[/IMG]

If that is your only partition, then you're right... lots of space. 

If you have other partitions on the drive, please post the output of

```
df -a
```

---

### Post by stav1953 on 2009-12-07
> **snowpine said:**
> If that is your only partition, then you're right... lots of space. 

If you have other partitions on the drive, please post the output of

```
df -a
```

These are all my partitions, thx

---

### Post by snowpine on 2009-12-07
> **stav1953 said:**
> These are all my partitions, thx

Your / (or "root") filesystem is 100% full.

I am not sure why it's called /dev/loop0. (On my computer, df -a lists /dev/sda3, the actual physical hard drive partition, as my / filesystem).

Since I do not understand your partitioning scheme, I'm afraid I'm out of suggestions. :(

---

### Post by stav1953 on 2009-12-07
> **snowpine said:**
> Your / (or "root") filesystem is 100% full.

I am not sure why it's called /dev/loop0. (On my computer, df -a lists /dev/sda3, the actual physical hard drive partition, as my / filesystem).

Since I do not understand your partitioning scheme, I'm afraid I'm out of suggestions. :(
I see that .!
And   I understand your concern ... Is there a program that would allow me to increase the size of this drive? alternatively, I could re-install windows home on another partition? but in all cases I was with the impressino that virtualbox is using expandable drives that could grow with the load of the files being installed. Hmmm, ... I could also re-install Ubuntu from scratch if necessary.
Any suggestions? In any case thanks for helping,
Stav

---

### Post by hawthornso23 on 2009-12-07
I don't know anything about running about virtual machines. But while searching for a solution to my sound problem I came across a thread on launchpad which suggests that people have been having trouble hosting these since upgrading from Jaunty to Karmic. Apparently there has been some sort of regression in the kernel which now runs at 100MHz whereas the old one ran at 250MHz which makes virtual machines run very slow. The same issue has been fingered as a possible cause of some of the sound problems people are having since upgrading to Karmic. 

Sorry I haven't got a link for you, but search launchpad and I'm sure you'll find it. If I were you I'd think about setting this up on Jaunty and not on Karmic until these issues are sorted out. Good Luck.

---

### Post by blues_1pt on 2009-12-08
I already went to [www.virtualbox.com](www.virtualbox.com) but i didn't find any closed-source version.........does anyone knows where to find it?

---

### Post by blues_1pt on 2009-12-08
I just found the binary and the open source versions.......sorry if i am a nub at it.

---

